# 34. Speeding Up Motif Finding

* A prefix of a length n string s is a substring s[1 : j]; a suffix of s is a substring s[k : n].

* The failure array of s is an array P of length n for which P[k] is the length of the longest substring s[j : k] 
that is equal to some prefix s[1 : k−j+1], where j cannot equal 1 (otherwise, P[k]would always equal k).

* By convention, P[1] = 0.

> **Given**    
> A DNA string s (of length at most 100 kbp) in FASTA format.

> **Return**    
>  The failure array of s.
 
```python

## 00. Set Variables

seq = ""


## 01. Read File

with open("rosalind_kmp.txt") as f :
	fr = f.readlines()
	for i in range(1, len(fr)) :
		seq += fr[i].replace("\n", "")


## 02. Find the Motif

f_arr = [0 for _ in range(len(seq))]

for i in range(1, len(seq)) :
	idx = 0
	
	if seq[i] == seq[0] :
		x = 2

		if f_arr[i] == 0 :
			f_arr[i] = 1	# when shared motif doesn't exist (1)

		while(i + x < len(seq) + 1) :
			if seq[i : i + x] == seq[0 : x] :
				if f_arr[i + x - 1] < x :
					f_arr[i + x - 1] = x	# when shared motif exists, add x
			
			else :
				break

			x += 1
      

## 03. Print the Result

for x in f_arr :
	print(x, end = " ")

```


## Link

> [Speeding Up Motif Finding](http://rosalind.info/problems/kmp)
