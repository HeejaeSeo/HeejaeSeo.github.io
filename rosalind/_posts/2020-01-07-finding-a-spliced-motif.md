# 11. Finding a Spliced Motif

* A subsequence of a string is a collection of symbols contained in order (though not necessarily contiguously) in the string (e.g., ACG is a subsequence of TATGCTAAGATC). 

* The indices of a subsequence are the positions in the string at which the symbols of the subsequence appear.

* Thus, the indices of ACG in TATGCTAAGATC can be represented by (2, 5, 9).

* As a substring can have multiple locations, a subsequence can have multiple collections of indices, and the same index can be reused in more than one appearance of the subsequence

  (ex. ACG is a subsequence of AACCGGTT in 8 different ways.)


> **Given**    
> Two DNA strings s and t (each of length at most 1 kbp) in FASTA format.

> **Return**    
> One collection of indices of s in which the symbols of t appear as a subsequence of s.    
If multiple solutions exist, you may return any one.
 
```python

## 00. Set Variables

start = 0
flag = 0
s = ""
idx_ls = []


## 01. Read File

with open("rosalind_sseq.txt", 'r') as f :
	fr = f.readlines()

	for i in range(1, len(fr)) :

		# Remove \n
		fr[i] = fr[i].replace("\n", "")

		# Concatenate s
		if fr[i].startswith(">") == 0 :
			s += fr[i]
		else :
			break

	# Designate t
	t = fr[len(fr) - 1]


## 02. Create Index

s_len = len(s)
t_len = len(t)


for i in range(t_len) :
	flag = 0

	for j in range(start, s_len) :
		if flag == 0 and t[i] == s[j] :
			idx_ls.append(j)
			start = j + 1
			flag = 1


## 03. Print Index List

for x in idx_ls :
	print(x + 1, end = ' ')

```


## Link

> [Finding a Spliced Motif](http://rosalind.info/problems/sseq/)
