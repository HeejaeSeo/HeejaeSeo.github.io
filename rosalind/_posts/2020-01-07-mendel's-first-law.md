# 12. Mendel's First Law

[Question](http://rosalind.info/problems/iprb/)


> **Given**    
> Three positive integers k, m, and n, representing a population containing k + m + n organisms.   
> **k** individuals are homozygous dominant for a factor, **m** are heterozygous, and **n** are homozygous recessive.

> **Return**    
> The probability that two randomly selected mating organisms will produce an individual possessing a dominant allele (and thus displaying the dominant phenotype).    
Assume that any two organisms can mate.
 
```python

## 01. Read File

with open("rosalind_iprb.txt", 'r') as f :
	fr = f.read().split()

# Designate k, m, n
k = int(fr[0])
m = int(fr[1])
n = int(fr[2])


## 02. Calculate Probability

total = k + m + n
deno = total * (total - 1)

sum1 = k * (k - 1) + m * (m - 1) * 0.75
sum2 = k * m * 2 + k * n * 2 + m * n 
nume = sum1 + sum2

result = float(nume / deno)


## 03. Print Probability

print(result)


```


## Link

> [Mendel's First Law](http://rosalind.info/problems/iprb/)
