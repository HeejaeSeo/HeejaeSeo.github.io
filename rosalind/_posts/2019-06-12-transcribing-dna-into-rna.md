# 02. Transcribing DNA into RNA

* An RNA string is a string formed from the alphabet containing 'A', 'C', 'G', and 'U'.

* Given a DNA string t corresponding to a coding strand, its transcribed RNA string u is formed 
by replacing all occurrences of 'T' in twith 'U' in u.


> **Given**
>  A DNA string t having length at most 1000 nt.

> **Return**
> The transcribed RNA string of t.
 
```python

## 01. Read File

with open("rosalind_rna.txt") as f :
	fr = f.readline()
	fr = fr.replace("\n", "")


## 02. Convert 'T' into 'U'

for s in fr :
	fr  = fr.replace("T", "U")


## 03. Print String

print(fr)

```


## Link

> [Transcribing DNA into RNA](http://rosalind.info/problems/rna/)
