# 14. Transitions and Transversions

* For DNA strings s1 and s2 having the same length, their transition/transversion ratio R(s1,s2)is the ratio of the total number of transitions to the total number of transversions, 
where symbol substitutions are inferred from mismatched corresponding symbols as when calculating Hamming distance.


> **Given**    
> Two DNA strings s1 and s2 of equal length (at most 1 kbp).

> **Return**    
> The transition / transversion ratio R(s1,s2).
 
```python

## 00. Set Variables

seq1 = ""
seq2 = ""
flag = 0
transition = 0
transversion = 0


## 01. Read File

with open("rosalind_tran.txt", 'r') as f :
	fr = f.readlines()

	for i in range(len(fr)) :

		# Remove \n
		fr[i] = fr[i].replace("\n", "")

		# Concatenate Sequence
		if fr[i].startswith(">") == 1 :
			flag += 1
			continue


		else :
			if flag == 1 :
				seq1 += fr[i]

			if flag == 2 :
				seq2 += fr[i]
        

## 02. Calculate Ratio (Transition / Transversion)

for i in range(len(seq1)) :

	if seq1[i] != seq2[i] :
		tmp_ls = [seq1[i], seq2[i]]
		tmp_sorted_ls = sorted(tmp_ls)

		if tmp_sorted_ls == ['A', 'G'] or tmp_sorted_ls == ['C', 'T'] :
			transition += 1
		else :
			transversion += 1

result = transition / transversion


## 03. Print Result

print(result)

```


## Link

> [Transitions and Transversions](http://rosalind.info/problems/tran/)
