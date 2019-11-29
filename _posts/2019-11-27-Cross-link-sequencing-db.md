---
layout: post
title:  "Cross linking biological databases and varaint call files analysis"
tags: [Coding, Bioinformatics]
---

Main topic of this post:
1. Converting genomic locations from VCF files to cDNA locations (in Python3.7)
2. From canonical transcript to cDNA locations and dealing with genes on different strands


##### Step one: Get gene sequence from databases 

INPUT: ENSG and ENST id \
OUTPUT: ENST, ENSG, CCDS, ccds_start, ccds_end, ccds_seq


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