# 26. Enumerating Oriented Gene Orderings

* A signed permutation of length n is some ordering of the positive integers {1, 2, …, n} in which each integer is then provided with either a positive or negative sign (for the sake of simplicity, we omit the positive sign). 

* For example, π = (5, −3, −2, 1, 4) is a signed permutation of length 5.


> **Given**    
> A positive integer n ≤ 6.

> **Return**    
> The total number of signed permutations of length n, followed by a list of all such permutations.  
(you may list the signed permutations in any order)
 
```python

## 00. Import Library

from itertools import permutations, product


## 01. Set Variables

case1 = 1	# case of permutation
case2 = 1	# whether positive or negative
idx_ls = [0, 1]
main_ls = []
pro_ls = []
result_ls = []


## 02. Read File

with open("rosalind_sign.txt") as f :
	fr = f.read()
	num = int(fr.replace("\n", ""))


## 03. Calculate the Number of Cases

for i in range(num) :
	case1 *= (i + 1)

for i in range(num) :
	case2 *= 2

case = case1 * case2


## 04. Calculate Permutations

for i in range(num) :
	main_ls.append([i + 1, (i + 1) * -1])

pro_idx_ls = list(product(idx_ls, repeat = num))

for i in range(len(pro_idx_ls)) :
	tmp_ls = []
	for j in range(num) :
		tmp = pro_idx_ls[i][j]
		tmp_ls.append(main_ls[j][tmp])

	pro_ls.append(tmp_ls)	

for x in pro_ls :
	per_ls = list(permutations(x))
	for y in per_ls :
		result_ls.append(list(y))

for x in result_ls :
	for i in range(len(x)) :
		if i == num - 1 :
			print(x[i])
		else :
			print(x[i], end = " ")

```


## Link

> [Enumerating Oriented Gene Orderings](http://rosalind.info/problems/sign/)
