# 22. Creating a Distance Matrix

* For two strings s1 and s2 of equal length, the p-distance between them, denoted dp(s1,s2), 
is the proportion of corresponding symbols that differ between s1 and s2.



> **Given**    
> A collection of n (n ≤ 10) DNA strings s1, … ,sn of equal length (at most 1 kbp).   
Strings are given in FASTA format.

> **Return**    
> The matrix D corresponding to the p-distance dp on the given strings.   
As always, note that your answer is allowed an absolute error of 0.001.
 
```python

## 00. Set Variables

string_ls = []
tmp = ""


## 01. Read File

with open("rosalind_pdst.txt") as f :
	fr = f.readlines()

	for i in range(len(fr)) :

		if fr[i].startswith(">") == 1 :
			if tmp != "" :
				string_ls.append(tmp)
				tmp = ""

		else :
			tmp += fr[i].replace("\n","")
			if i == len(fr) - 1 :
				string_ls.append(tmp)


## 02. Create a Distance Matrix

str_cnt = len(string_ls)
str_len = len(string_ls[0])

pro_arr = [[0 for _ in range(str_cnt)] for _ in range(str_cnt)]

for i in range(str_cnt - 1) :
	for j in range(i + 1, str_cnt) :
		tmp_sum = 0
		for k in range(0, str_len) :
			if string_ls[i][k] != string_ls[j][k] :
				tmp_sum += 1
		tmp_pro = tmp_sum / str_len
		pro_arr[i][j] = tmp_pro
		pro_arr[j][i] = tmp_pro


## 03. Print the Matrix

for x in pro_arr :
	for y in x :
		print(y, end = " ")
	print("")


```


## Link

> [Creating a Distance Matrix](http://rosalind.info/problems/pdst/)
