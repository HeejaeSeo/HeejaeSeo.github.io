# 35. Maximum Matchings and RNA Secondary Structures

* The graph theoretical analogue of the quandary stated in the introduction above is that if we have an RNA string s that does not have the same number of occurrences of 'C' as 'G' and the same number of occurrences of 'A' as 'U', then the bonding graph of s cannot possibly possess a perfect matching among its basepair edges.

* In light of this fact, we define a maximum matching in a graph as a matching containing as many edges as possible. 

* A maximum matching of basepair edges will correspond to a way of forming as many base pairs as possible in an RNA string.


> **Given**    
> An RNA string s of length at most 100.

> **Return**    
> The total possible number of maximum matchings of basepair edges in the bonding graph of s.
 
```python

## 00. Define Function

def multi(x, y) :
	answer = 1

	n1 = max(x, y)
	n2 = min(x, y)
	
	for i in range(n2) :
		answer *= n1
		n1 -= 1

	return answer


## 01. Set Variables

seq = ""
base_dic = {'A' : 0, 'U' : 0, 'G' : 0, 'C' : 0}


## 02. Read File

with open("rosalind_mmch.txt") as f :
	fr = f.readlines()

	for i in range(1, len(fr)) :
		seq += fr[i].replace("\n", "")


## 03. Count the Number of Bases

for base, cnt in base_dic.items() :
	base_dic[base] = seq.count(base)


## 04. Calculate the Number of Maximum Matchings

resultAU = multi(base_dic['A'], base_dic['U'])
resultGC = multi(base_dic['G'], base_dic['C'])

result = resultAU * resultGC

print(result)

```


## Link

> [Maximum Matchings and RNA Secondary Structures](http://rosalind.info/problems/mmch/)
