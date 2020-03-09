# 16. Enumerating Gene Orders

* A permutation of length n is an ordering of the positive integers {1, 2, …, n}. 

* For example, π=(5, 3, 2, 1, 4)is a permutation of length 5.


> **Given**    
>  A positive integer n ≤ 7.

> **Return**    
> The total number of permutations of length n, followed by a list of all such permutations (in any order).
 
```python

## 00. Import Library
from itertools import permutations


## 01. Set Variables
num_ls = []
result = 1


## 02. Read File
with open("rosalind_perm.txt") as f :
	fr = f.read()
	num = int(fr.replace("\n", ""))
  
  
## 03. Create num_ls
for i in range(num) :
	num_ls.append(i + 1)


## 04. Calculate Permutation
for i in range(num) :
	result *= (i + 1)

print(result)


## 05. Print Permutation Result
com_ls = list(permutations(num_ls, num))

for i in range(result) :
	for j in range(len(com_ls[i])) :
		print(com_ls[i][j], end = " ")
	print("")


```


## Link

> [Enumerating Gene Orders](http://rosalind.info/problems/perm/)
