# 25. Finding a Shared Motif

* A common substring of a collection of strings is a substring of every member of the collection. 

* We say that a common substring is a longest common substring if there does not exist a longer common substring. 

* For example, "CG" is a common substring of "ACGTACGT" and "AACCGTATA", but it is not as long as possible;  
in this case, "CGTA" is a longest common substring of "ACGTACGT" and "AACCGTATA".

* Note that the longest common substring is not necessarily unique.

* For a simple example, "AA" and "CC" are both longest common substrings of "AACC" and "CCAA".


> **Given**    
> A collection of k (k ≤ 100) DNA strings of length at most 1 kbp each in FASTA format.

> **Return**    
> A longest common substring of the collection. (If multiple solutions exist, you may return any single solution.)
 
```python

## 00. Set Variables

string_ls = []
com_ls = []
string = ""
cnt = 0


## 01. Read File

with open("rosalind_lcsm.txt", 'r') as f :
	fr = f.readlines()

	for i in range(len(fr)) :
		if fr[i].startswith(">") :

			if string != "" :
				string_ls.append(string)
				string = ""

		else :
			fr[i] = fr[i].replace("\n", "")
			string += fr[i]
			
			if i == (len(fr) - 1):
				string_ls.append(string)


## 02. Find Common String - 1st

s1 = string_ls[0]
s2 = string_ls[1]

for i in range(len(s1) - 1) :
	for j in range(len(s2) - 1) :
		if s1[i : i + 2] == s2[j : j + 2] :
			com_ls.append(s1[i : i + 2])
			x = i + 2
			y = j + 2
			while(x < len(s1) and y < len(s2)) :
				if s1[x] == s2[y] :
					com_ls.append(s1[i : x + 1])
					x += 1
					y += 1
				else :
					break
          
          
## 03. Find Common String - Else

for i in range(2, len(string_ls)) :
	for j in range(len(com_ls) - 1, -1, -1) :
		if com_ls[j] not in string_ls[i] :
			com_ls.remove(com_ls[j])


## 04. Find the Longest Common Substring

for x in com_ls :
	if len(x) > cnt :
		result = x
		cnt = len(x)
    
print(result)

```


## Link

> [Finding a Shared Motif](http://rosalind.info/problems/lcsm/)
