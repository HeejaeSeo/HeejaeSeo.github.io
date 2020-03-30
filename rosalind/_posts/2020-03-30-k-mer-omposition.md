# 32. k-Mer Composition

* For a fixed positive integer k, order all possible k-mers taken from an underlying alphabet lexicographically.

* Then the k-mer composition of a string s can be represented by an array A for which A[m] denotes the number of times that the mth k-mer
(with respect to the lexicographic order) appears in s.

> **Given**    
>  A DNA string s in FASTA format (having length at most 100 kbp).

> **Return**    
> The 4-mer composition of s.
 
```python

## 00. Set Variables

seq = ""
kmer_ls = []
result_ls = [0 for _ in range(256)]
base_dic = {'A' : 0, 'C' : 1, 'G' : 2, 'T' : 3}


## 01. Read File

with open("rosalind_kmer.txt") as f :
	fr = f.readlines()
  
	for i in range(1, len(fr)) :
		seq += fr[i].replace("\n", "")


## 02. Get the k-Mer Compositions

for i in range(len(seq) - 3) :
	tmp = seq[i : i + 4]
	kmer_ls.append(tmp)

for frag in kmer_ls :
	idx = 0

	for i in range(len(frag)) :

		tmp_x = base_dic[frag[i]]
		tmp_y = 4 ** (3 - i)

		idx = idx + tmp_x * tmp_y

	result_ls[idx] += 1
  

## 03. Print the Result

for x in result_ls :
	print(x, end = " ")

```


## Link

> [k-Mer Composition](http://rosalind.info/problems/kmer/)
