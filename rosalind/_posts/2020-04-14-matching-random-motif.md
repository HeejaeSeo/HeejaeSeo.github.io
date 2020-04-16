# 39. Matching Random Motifs

[Question](http://rosalind.info/problems/rstr/)


> **Given**    
> A positive integer N ≤ 100000, a number x between 0 and 1, and a DNA string s of length at most 10 bp.

> **Return**    
> The probability that if N random DNA strings having the same length as s are constructed with GC-content x,
then at least one of the strings equals s.  
We allow for the same random string to be created more than once.
 
 
```python

## 00. Set Variables

tmp = 1
seq_dic = {'A' : 0, 'T' : 0, 'G' : 0, 'C' : 0}


## 01. Read File

with open("rosalind_rstr.txt") as f :
	fr = f.read().split()

	n = int(fr[0])
	x = float(fr[1])
	seq = fr[2]


## 02. Get Data

gc = x / 2
at = (1 - x) / 2

for x in seq :
	seq_dic[x] += 1


## 03. Calculate the Probability

tmp = at ** (seq_dic['A'] + seq_dic['T']) * gc ** (seq_dic['G'] + seq_dic['C'])
result = round(1 - ((1 - tmp) ** n), 3)

print(result)

```


## Link

> [Matching Random Motifs](http://rosalind.info/problems/rstr/)
