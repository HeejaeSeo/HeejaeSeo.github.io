# 19. Consensus and Profile

[Question](http://rosalind.info/problems/cons/)


> **Given**    
> A collection of at most 10 DNA strings of equal length (at most 1 kbp) in FASTA format.

> **Return**    
> A consensus string and profile matrix for the collection.    
(If several possible consensus strings exist, then you may return any one of them.)
 
```python

## 00. Set Variables

string_ls = []
max_ls = []
idx_ls = []
string = ""
consensus = ""
dic = {"A" : 0, "C" : 1, "G" : 2, "T" : 3}


## 01. Read File

with open("rosalind_cons.txt") as f :
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


## 02. Create Profile Matrix

profile = [[0 for _ in range(len(string_ls[0]))] for _ in range(4)]
prof_len = len(profile[0])

for x in string_ls :
	for i in range(len(x)) :
		aa = dic[x[i]]
		profile[aa][i] += 1
    
    
## 03. Create Consensus String Index

for i in range(prof_len) :
	max_ls.append(max(profile[0][i], profile[1][i], profile[2][i], profile[3][i]))

for i in range(len(max_ls)) :
	for j in range(prof_len) :
		if profile[j][i] == max_ls[i] :
			idx_ls.append(j)
			break
      
      
## 04. Print Consensus String

for x in idx_ls :
	for aa, idx in dic.items() :
		if idx == x :
			consensus += aa
			break

print(consensus)

```


## Link

> [Consensus and Profile](http://rosalind.info/problems/cons/)
