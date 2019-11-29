---
layout: post
title:  "Cross linking biological databases and varaint call files analysis (Python3 examples)"
tags: [Coding, Bioinformatics]
---

#### Main topic of this post:

1. Converting genomic locations from VCF files to cDNA locations (in Python3.7)
2. From canonical transcript to cDNA locations and dealing with genes on different strands

In my example below, I am trying to show how to get all the information starting from the knowncanonical.txt file

Please find the download link to the final output below.

#### Step one: Get gene name and CCDS ID from ENSEMBL 

INPUT: ENSG and ENST id \
OUTPUT: CCDS_ID and HNGC gene name

```python

def get_gene_name(ensg, enst):
    """
    Get gene name based on ENSG
    Get CCDS id based on ENST
    
    All info are from ENSEMBL db
    """
    server = "https://rest.ensembl.org"
    ext= "/xrefs/id/"+ensg+"?external_db=HGNC"

    r = requests.get(server+ext, headers={ "Content-Type" : "application/json"})

    while not r.ok:
        time.sleep(200)
        r = requests.get(server+ext, headers={ "Content-Type" : "application/json"})
                       
    decoded = r.json()[0]
    gene_symbol = decoded["display_id"]

    
    ext = "/xrefs/id/"+enst+"?external_db=CCDS"
    r = requests.get(server+ext, headers={ "Content-Type" : "application/json"})

    while not r.ok:
        time.sleep(200)
        r = requests.get(server+ext, headers={ "Content-Type" : "application/json"})
                       
    decoded = r.json()[0]
    
    ccds_id = decoded["display_id"]
    return gene_symbol, ccds_id

```

#### Step two: Get CDS sequences and positions from CCDS database

INPUT: CCDS id, CCDS current version (Link to download)\
OUTPUT: 

```python

# Get DNA sequences from UCSC genome browser
def get_dna(chrom, start, end):
    """
    get dna sequences from ucsc genome browser based on 
    chrom (in the format: chr*), start, end
    """
    server="https://api.genome.ucsc.edu/" 
    ext = f"getData/sequence?genome=hg38;chrom={chrom};start={start};end={end+1}"
    print(ext)
    r = requests.get(server+ext, headers={"Content-Type": "application/json"})
                                
    while not r.ok:
        #r.raise_for_status()
        print(r)
        time.sleep(200)
        r = requests.get(server+ext, headers={"Content-Type": "application/json"})
                                                                   
    decoded = r.json()
    dna_seq = Seq(decoded["dna"], generic_dna)
                                                                               
    return dna_seq

```