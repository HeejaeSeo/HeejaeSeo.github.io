# 40. Expected Number of Restriction Sites

[Question](http://rosalind.info/problems/eval/)


> **Given**    
> A positive integer n (n ≤ 1,000,000), a DNA string s of even length at most 10, and an array A of length at most 20, containing numbers between 0 and 1.

> **Return**    
> An array B having the same length as A in which B[i] represents the expected number of times 
that s will appear as a substring of a random DNA string t of length n, where t is formed with GC-content A[i].
 
```python

## 00. Set Variables

result_ls = []


## 01. Read File

with open("rosalind_eval.txt") as f :
	fr = f.read().strip().split("\n")

	n = int(fr[0])
	seq = fr[1]
	prob_ls = fr[2].split(" ")

	seq_len = len(seq)


## 02. Calculate the Probability

for x in prob_ls :
	gc = float(x) / 2
	at = (1 - float(x)) / 2
	result = 1

	for s in seq :
		if s == "A" or s == "T" :
			result *= at
      
		else :
			result *= gc

	result *= (n - seq_len + 1)	# the number of cases where the substring exists
	
	result_ls.append(result)


## 03. Print the Result

for x in result_ls :
	print(x, end = " ")

```


## Link

> [Expected Number of Restriction Sites](http://rosalind.info/problems/eval/)
