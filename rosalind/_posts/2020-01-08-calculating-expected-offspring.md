# 13. Calculating Expected Offspring

[Question](http://rosalind.info/problems/iev/)


> **Given**    
> Six nonnegative integers, each of which does not exceed 20,000.  
The integers correspond to the number of couples in a population possessing each genotype pairing for a given factor.   
In order, the six given integers represent the number of couples having the following genotypes:
> 1. AA-AA   
> 2. AA-Aa   
> 3. AA-aa   
> 4. Aa-Aa   
> 5. Aa-aa   
> 6. aa-aa   

> **Return**    
> The expected number of offspring displaying the dominant phenotype in the next generation, 
under the assumption that every couple has exactly two offspring.
 
```python

## 00. Set Variables

ls_prob = [1, 1, 1, 3/4, 1/2, 0]
ls_factor = []
result = 0


## 01. Read File

with open("rosalind_iev.txt", 'r') as f :
	fr = f.read().split()
	
for i in range(len(fr)) :
	ls_factor.append(int(fr[i]))


## 02. Calculate Expectation Mean

for i in range(6) :
	result += ls_prob[i] * ls_factor[i]

result *= 2


## 03. Print Result

print(result)


```


## Link

> [Calculating Expected Offspring](http://rosalind.info/problems/iev/)
