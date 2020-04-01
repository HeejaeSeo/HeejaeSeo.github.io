# 33. Genome Assembly as Shortest Superstring

* For a collection of strings, a larger string containing every one of the smaller strings as a substring is called a superstring.

* By the assumption of parsimony, a shortest possible superstring over a collection of reads serves as a candidate chromosome.


> **Given**    
>  At most 50 DNA strings of approximately equal length, not exceeding 1 kbp, in FASTA format.   
(which represent reads deriving from the same strand of a single linear chromosome)  
The dataset is guaranteed to satisfy the following condition : there exists a unique way to reconstruct the entire chromosome from these reads by gluing together pairs of reads that overlap by more than half their length.

> **Return**    
> A shortest superstring containing all the given strings. (thus corresponding to a reconstructed chromosome)
 
```python

## 00. Set Variables

seq_ls = []
tmp_seq = ""


## 01. Read File

with open("rosalind_long.txt") as f :
	fr = f.readlines()

	for i in range(1, len(fr)) :

		if fr[i].startswith(">") :
			seq_ls.append(tmp_seq)
			tmp_seq = ""
		else :
			tmp_seq += fr[i].replace("\n", "")

	seq_ls.append(tmp_seq)


## 02. Get the Shortest Superstring

std = seq_ls[0]			# standard seq
half = round(len(std) / 2) 	# half length of standard seq
seq_ls.remove(seq_ls[0])	# Eliminate standard seq in seq_ls

while(seq_ls) :
	for x in seq_ls :	# seq to iterate

		for j in range(len(x) - half) :		
			if x[j : j + half] in std :
				frag = x[j : j + half]

				start_idx = std.index(frag)
				end_idx = std.index(frag) + half

				prev = max(x[: j], std[: start_idx])
				after = max(x[j + half :], std[end_idx :])

				std = prev + x[j : j + half] + after				
				seq_ls.remove(seq_ls[seq_ls.index(x)])
				break
        
print(std)


```


## Link

> [Genome Assembly as Shortest Superstring](http://rosalind.info/problems/long/)
