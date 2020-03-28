# 31. Enumerating k-mers Lexicographically

* Assume that an alphabet 𝒜 has a predetermined order;   
that is, we write the alphabet as a permutation 𝒜 = (a1, a2, …, ak), where a1 < a2 < ⋯ <ak. 

* For instance, the English alphabet is organized as (A, B, …, Z).

* Given two strings s and t having the same length n, 
we say that s precedes t in the lexicographic order if the first symbol s[j].


> **Given**    
> A collection of at most 10 symbols defining an ordered alphabet, and a positive integer n(n ≤ 10).

> **Return**    
> All strings of length n that can be formed from the alphabet, ordered lexicographically.   
(Use the standard order of symbols in the English alphabet)
 
```python

## 00. Import Library

from itertools import product


## 01. Set Variables

result_ls = []


## 02. Read File

with open("rosalind_lexf.txt") as f :
	fr = f.readlines()

	seq_ls = fr[0].replace("\n", "").split(" ")
	n = int(fr[1])


## 03. Get the Result

result = list(product(seq_ls, repeat = 3))

for x in result :

	for i in range(len(x)) :
  
		print(x[i], end = "")
    
	print("")



```


## Link

> [Enumerating k-mers Lexicographically](http://rosalind.info/problems/lexf/)
