# 08. Overlap Graphs

* A graph whose nodes have all been labeled can be represented by an adjacency list, in which each row of the list contains the two node labels corresponding to a unique edge.

* A directed graph (or digraph) is a graph containing directed edges, each of which has an orientation. 

* That is, a directed edge is represented by an arrow instead of a line segment; the starting and ending nodes of an edge form its tail and head, respectively. 

* The directed edge with tail vand head w is represented by (v,w)
  (but not by (w,v)). 

* A directed loop is a directed edge of the form (v,v).

* For a collection of strings and a positive integer k, the overlap graph for the strings is a directed graph 
in which each string is represented by a node, and string s is connected to string t with a directed edge 
when there is a length k suffix of s that matches a length k prefix of t, as long as s≠t

* We demand s≠t to prevent directed loops in the overlap graph (although directed cycles may be present).


> **Given**
> A collection of DNA strings in FASTA format having total length at most 10 kbp.

> **Return**
> The adjacency list corresponding to O3. You may return edges in any order.
 
```python

## 00. Set Variables

id_ls = []
seq_ls = []


## 01. Read File

with open("rosalind_grph.txt") as f :
    fr = f.read()

data_ls = fr.split("\n")
data_ls_len = len(data_ls)


## 02. Create id-seq list

for i in range(data_ls_len) :

    # Create id list
    if i % 3 == 0 :
        data_ls[i] = data_ls[i].replace(">","")
        id_ls.append(data_ls[i])

    # Create seq list
    if i % 3 == 1 :
        join = data_ls[i] + data_ls[i + 1]
        seq_ls.append(join)


## 03. Print Overlap Strand ID

for i in range(len(id_ls) - 1) :
    for j in range(id_ls_len - 1) :
        if i != j :
            if seq_ls[i][-3 :] == seq_ls[j][0 : 3] :
                print("%s %s" %(id_ls[i], id_ls[j]))


```


## Link

[Overlap Graphs](http://rosalind.info/problems/grph/)
