# 38. Introduction to Alternative Splicing

[Question](http://rosalind.info/problems/aspc/)


> **Given**    
>  Positive integers n and m with 0 ≤ m ≤ n ≤ 2000.

> **Return**    
> The sum of combinations C(n,k) for all k satisfying m ≤ k ≤ n, modulo 1,000,000. In shorthand, ∑nk = m(nk).
 
```python

## 00. Import Library

import math


## 01. Set Variables

result = 0


## 02. Define Function

def comb(n, r) :
	result = math.factorial(n) / (math.factorial(n - r) * math.factorial(r))
	result %= 1000000

	return result


## 03. Read File

with open("rosalind_aspc.txt") as f :
	n, m = map(int, f.read().strip().split(" "))
  

## 04. Add the Number of Combination

for i in range(m, n + 1) :
	result += comb(n, i)

result %= 1000000

print(result)

```


## Link

> [Introduction to Alternative Splicing](http://rosalind.info/problems/aspc/)
