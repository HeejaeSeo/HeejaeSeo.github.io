# 21. Completing a Tree

* An undirected graph is connected if there is a path connecting any two nodes. 

* A tree is a connected (undirected) graph containing no cycles.

* This definition forces the tree to have a branching structure organized around a central core of nodes, just like its living counterpart. 

* In the creation of a phylogeny, taxa are encoded by the tree's leaves, or nodes having degree 1. 

* A node of a tree having degree larger than 1 is called an internal node.

> **Given**    
>  A positive integer n (n ≤ 1000) and an adjacency list corresponding to a graph on n nodes that contains no cycles.

> **Return**    
>  The minimum number of edges that can be added to the graph to produce a tree.
 
```python

## 00. Set Variables

adj_ls = []
tmp_ls = [[0]]


## 01. Read File

with open("rosalind_tree.txt") as f :
	fr = f.readlines()
	for i in range(len(fr)) :
		adj_ls.append(fr[i].replace("\n", ""))
		if i == 0 :
			num = int(fr[i])
	adj_ls.remove(adj_ls[0])


## 02. Get the Minimun Number of Edges

num_ls = [str(x) for x in range(1, num + 1)]

for i in range(len(adj_ls)) :
	n1, n2 = adj_ls[i].split(" ")
	j = 0

	while(j < len(tmp_ls)) :
		flag = 0
		flag = removeItem(n1, n2, j)

		if n1 in tmp_ls[j]  :
			flag = 1
			tmp_ls[j].append(n2)
			if n2 in num_ls :
				num_ls.remove(n2)
			else :
				for k in range(len(tmp_ls)) :
					if n1 not in tmp_ls[k] and n2 in tmp_ls[k] :
						new_ls = list(set(tmp_ls[j]) | set(tmp_ls[k]))

						if j < k :
							tmp_ls.remove(tmp_ls[k])
							tmp_ls.remove(tmp_ls[j])
						else :
							tmp_ls.remove(tmp_ls[j])
							tmp_ls.remove(tmp_ls[k])
						tmp_ls.append(new_ls)
						break
			break

		if n2 in tmp_ls[j] :
			flag = 1
			tmp_ls[j].append(n1)
			if n1 in num_ls :
				num_ls.remove(n1)
			else :
				for k in range(len(tmp_ls)) :
					if n2 not in tmp_ls[k] and n1 in tmp_ls[k] :
						new_ls = list(set(tmp_ls[j]) | set(tmp_ls[k]))

						if j < k :
							tmp_ls.remove(tmp_ls[k])
							tmp_ls.remove(tmp_ls[j])
						else :
							tmp_ls.remove(tmp_ls[j])
							tmp_ls.remove(tmp_ls[k])
						tmp_ls.append(new_ls)
						break
			break

		j += 1

	if flag == 0 :
		tmp = [n1, n2]
		tmp_ls.append(tmp)

		num_ls.remove(n1)
		num_ls.remove(n2)
    

## 03. Print the Number of Edges

edge_num = len(num_ls) - 1 + len(tmp_ls) - 1    
# -1 for degree between the number of (num_ls) nodes / -1 for initial element [0] in tmp_ls
print(edge_num)

```


## Link

> [Completing a Tree](http://rosalind.info/problems/tree/)
