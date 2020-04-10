# 37. Introduction to Set Operations

* If A and B are sets, then their union A ∪ B is the set comprising any elements in either A or B; 
their intersection A ∩ B is the set of elements in both A and B; 
and their set difference A − B is the set of elements in A but not in B.

* Furthermore, if A is a subset of another set U, then the set complement of A with respect to U is defined as the set Ac = U − A.


> **Given**    
> A positive integer n (n ≤ 20,000) and two subsets A and B of {1, 2, …, n}.

> **Return**    
> Six sets : A ∪ B, A ∩ B, A − B, B − A, Ac, and Bc (where set complements are taken with respect to {1, 2, …, n}.

```python

## 01. Read File

with open("rosalind_seto.txt") as f :
	fr = f.readlines()
	num = int(fr[0].replace("\n", ""))


## 02. Create Subsets and a Total Set

A_ls = fr[1].replace("{", "").replace("}", "").split(",")
B_ls = fr[2].replace("{", "").replace("}", "").split(",")

A = set([int(x) for x in A_ls])
B = set([int(x) for x in B_ls])

total_ls = [x for x in range(1, num+ 1)]
C = set(total_ls)


## 03. Calculate Set Operations and Print the Result

r1 = A | B
r2 = A & B
r3 = A - B
r4 = B - A
r5 = C - A
r6 = C - B

print(r1)
print(r2)
print(r3)
print(r4)
print(r5)
print(r6)

```


## Link

> [Introduction to Set Operations](http://rosalind.info/problems/seto/)
