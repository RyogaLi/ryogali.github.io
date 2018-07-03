---
layout: post
title:  "Distance between strings with python examples"
tags: [Machine Learning, Ongoing]
---

### Distance between strings ###

Here I describe four different algorithems to calculate distance between two strings(sequences) with python code examples.

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

#### 2. Levenshtein distancebetween two strings is no greater than the sum of their ####

It measures the difference between two sequences. The distance between two words is the minimum number of single-character edits (insertions, deletions or substitutions) required 
to change one word into the other. 

$$\qquad \operatorname {lev} _{a,b}(i,j)={\begin{cases}\max(i,j)&{\text{ if }}\min(i,j)=0,\\\min {\begin{cases}\operatorname {lev} _{a,b}(i-1,j)+1\\\operatorname {lev} _{a,b}(i,j-1)+1\\\operatorname {lev} _{a,b}(i-1,j-1)+1_{(a_{i}\neq b_{j})}\end{cases}}&{\text{ otherwise.}}\end{cases}} $$

* It is at least the difference of the sizes of the two strings
* It is at most the length of the longer string
* The Levenshtein distancebetween two strings is no greater than the sum of their Levenshtein distances from a third string

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

#### 3. Jaro–Winkler distance ####

The Jaro similarity $$ sim_{j} $$ of two strings $$s_1$$ and $$s_2$$ is defined as:

%$$ sim_{j}=\left\{{\begin{array}{l l}0&{\text{if }}m=0\\{\frac {1}{3}}\left({\frac {m}{|s_{1}|}}+{\frac {m}{|s_{2}|}}+{\frac {m-t}{m}}\right)&{\text{otherwise}}\end{array}}\right. $$

Where:

* $$|s_{i}|$$ is the length of the string $$s_{i}$$
* $$m$$ is the number of matching characters
* $$t$$ is half the number of **transpositions**. Each character of $$ s_{1} $$ is compared with all its matching characters in  $$ s_{2} $$. The number of matching (but different sequence order) characters divided by 2 defines the number of transpositions.

The Jaro–Winkler similarity $$ sim_{j} $$ of two strings $$s_1$$ and $$s_2$$ is defined as: