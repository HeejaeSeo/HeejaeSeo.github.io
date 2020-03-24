# 27. Independent Alleles

[Question](http://rosalind.info/problems/lia/)


> **Given**    
> Two positive integers k(k ≤ 7) and N(N ≤ 2^k).   
In this problem, we begin with Tom, who in the 0th generation has genotype Aa Bb.   
Tom has two children in the 1st generation, each of whom has two children, and so on.  
Each organism always mates with an organism having genotype Aa Bb.

> **Return**    
> The probability that at least N Aa Bb organisms will belong to the k-th generation of Tom's family tree.  
(Don't count the Aa Bb mates at each level).   
Assume that Mendel's second law holds for the factors.
 
```python

## 00. Import Library

from functools import reduce
import operator as op


## 01. Define Function

def countComb(n, r) :
	r = min(r, n - r) 

	x = reduce(op.mul, range(n, n - r, -1) , 1)
	y = reduce(op.mul, range(1, r + 1), 1)

	answer = x / y
	return answer


## 02. Set Variables

result = 0


## 03. Read File

with open("rosalind_lia.txt") as f :
	fr = f.readline()
	k = int(fr.split(" ")[0])
	n = int(fr.split(" ")[1])


## 03. Process

total = 2 ** k

for i in range(n, total + 1) :
	tmp = 1

	for j in range(i) :
		tmp *= 1/4
	
	for j in range(total - i) :
		tmp *= 3/4

	tmp *= countComb(total, i)

	result += tmp


## 04. Print Result

print(result)
```


## Link

> [Independent Alleles](http://rosalind.info/problems/lia/)
