# 23. Counting Phylgenetic Ancestors

* A binary tree is a tree in which each node has degree equal to at most 3. 

* The binary tree will be our main tool in the construction of phylogenies.

* Even though a binary tree can include nodes having degree 2, an unrooted binary tree is defined more specifically : all internal nodes have degree 3. 

* In turn, a rooted binary tree is such that only the root has degree 2 (all other internal nodes have degree 3).


> **Given**    
> A positive integer n (3 ≤ n ≤ 10000).

> **Return**    
> The number of internal nodes of any unrooted binary tree having n leaves.
 
```python

## 01. Read File

with open("rosalind_inod.txt") as f :
	fr = f.readline()
	leaf_cnt = fr.replace("\n", "")


## 02. Print the Result

internal_node_cnt = int(leaf_cnt) - 2
print(internal_node_cnt)


```


## Link

> [Counting Phylogenetic Ancestors](http://rosalind.info/problems/inod/)
