---
layout: post
title:  "Distance between strings with python examples"
tags: [Machine Learning, Bioinformatics]
---

### Distance between strings ###

Here I describe some different algorithems to calculate distance between two strings(sequences) with python code examples.

---

#### 1. Hamming distance ####

In information theory, the Hamming distance between two strings of **equal lentgh** is the number of positions at which the corresponding symbols are different.
It measures the number of postions iwht mismatching characters. 

{% highlight python %}

A = "CGGAGG" 
B = "AGGTGG"

def hamming_dis(A, B):
	assert len(A) == len(B) # we need the strings to have same len
	return sum(ch1 != ch2 for ch1, ch2 in zip(A, B)) # in this case the distance is 2

{% endhighlight %}

---

#### 2. Levenshtein distance ####

It measures the difference between two sequences. The distance between two words is the minimum number of single-character edits (insertions, deletions or substitutions) required 
to change one word into the other. 

* It is at least the difference of the sizes of the two strings
* It is at most the length of the longer string
* The Levenshtein distance between two strings is no greater than the sum of their Levenshtein distances from a third string

{% highlight python %}

# Here is a function that calculates the distance between s and t recursively
def LD(s, t):
    if s == "":
        return len(t)
    if t == "":
        return len(s)
    if s[-1] == t[-1]:
        cost = 0
    else:
        cost = 1
       
    res = min([LD(s[:-1], t)+1,
               LD(s, t[:-1])+1, 
               LD(s[:-1], t[:-1]) + cost])
    return res

# we can also compute the distance iteratively
# in this case, we can put different costs for deletion, insertion and substitution
def iterative_levenshtein(s, t, costs=(1, 1, 1)):
    """ 
        iterative_levenshtein(s, t) -> ldist
        ldist is the Levenshtein distance between the strings 
        s and t.
        For all i and j, dist[i,j] will contain the Levenshtein 
        distance between the first i characters of s and the 
        first j characters of t
        
        costs: a tuple or a list with three integers (d, i, s)
               where d defines the costs for a deletion
                     i defines the costs for an insertion and
                     s defines the costs for a substitution
    """
    rows = len(s)+1
    cols = len(t)+1
    deletes, inserts, substitutes = costs
    
    dist = [[0 for x in range(cols)] for x in range(rows)]
    # source prefixes can be transformed into empty strings 
    # by deletions:
    for row in range(1, rows):
        dist[row][0] = row * deletes
    # target prefixes can be created from an empty source string
    # by inserting the characters
    for col in range(1, cols):
        dist[0][col] = col * inserts
        
    for col in range(1, cols):
        for row in range(1, rows):
            if s[row-1] == t[col-1]:
                cost = 0
            else:
                cost = substitutes
            dist[row][col] = min(dist[row-1][col] + deletes,
                                 dist[row][col-1] + inserts,
                                 dist[row-1][col-1] + cost) # substitution
 #   for r in range(rows):
 #       print(dist[r])
    
 
    return dist[row][col]
# default:
print(iterative_levenshtein("abc", "xyz"))
# the costs for substitions are twice as high as inserts and delets:
print(iterative_levenshtein("abc", "xyz", costs=(1, 1, 2)))
# inserts and deletes are twice as high as substitutes
print(iterative_levenshtein("abc", "xyz", costs=(2, 2, 1)))

{% endhighlight %}

---

#### 3. Damerau–Levenshtein distance ####

Compare to the classical Levenshtein distance, this algorithm also includes transpositions of two adjacent characters. It is closely realated to Needleman–Wunsch algorithm and 
Smith–Waterman algorithm which are mostly used in seuqnce alignment (global and local).


---

#### 4. Jaro–Winkler distance ####

The Jaro algorithm is a measure of characters in common, when they are no more than half the length of the longer string in distance, with consideration for transpositions.
Winkler modified this algorithm to support the idea that differences near the start of the string are more significant than differences near the end of the string. 


--- 

#### 5. Simple approach - Python lib **difflib** ####

[From the documentation](https://docs.python.org/3.4/library/difflib.html#difflib.get_close_matches)

{% highlight python %}
import difflib
# difflib.get_close_matches(word, possibilities, n, cutoff)
# word: a sequence for which close matches are desired
# possibilities: possibilities is a list of sequences
# n (default 3) is the maximum number of close matches to return; n must be greater than 0
# cutoff (default 0.6) is a float in the range [0, 1]. Possibilities that don’t score at least that similar to word are ignored.

a = "NNNNNACTNNN"
seqs = ["CTGGAACTACC", "GTGTACGACCC"]
return = difflib.get_close_matches(a, b, 1, 0.2)
# ['CTGGAACTACC']
# in this case we accept cutoff >= 0.2 (3bp match out of 11)
{% endhighlight %}