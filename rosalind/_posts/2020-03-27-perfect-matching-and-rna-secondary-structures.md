# 30. Perfect Matching and RNA Secondary Structures

[Question](http://rosalind.info/problems/pmch)


> **Given**    
> An RNA string s of length at most 80 bp having the same number of occurrences of 'A' as 'U' 
and the same number of occurrences of 'C' as 'G'.

> **Return**    
>  The total possible number of perfect matchings of basepair edges in the bonding graph of s.
 
```python

## 00. Set Variables

cntAU = cntGC = 0
seq = ""


## 01. Read File

with open("rosalind_pmch.txt") as f :
	fr = f.readlines()


## 02. Count the Number of Bases

for i in range(1, len(fr)) :
	seq += fr[i].replace("\n", "")

for x in seq :
	if x == "A" :
		cntAU += 1

	elif x == "G" :
		cntGC += 1
		
	else :
		continue


## 03. Calculate the Number of Perfect Matching

factAU = factGC = 1

for i in range(1, cntAU + 1) :
	factAU *= i

for i in range(1, cntGC + 1) :
	factGC *= i

result = factAU * factGC

print(result)

```


## Link

> [Perfect Matching and RNA Secondary Structures](http://rosalind.info/problems/pmch)
