# 01. Counting DNA Nucleotides

* A string is simply an ordered collection of symbols selected from some alphabet and formed into a word.

* The length of a string is the number of symbols that it contains.



> **Given**
> A DNA string s of length at most 1000 nt.

> **Return**
> Four integers (separated by spaces) counting the respective number of times that the symbols 
'A', 'C', 'G', and 'T' occur in s.
 
```python

## 01. Read File

with open("rosalind_dna.txt") as f :
	fr = f.readline()
	fr = fr.replace("\n", "")


## 02. Count the Number of Bases

cnt_a = fr.count("A")
cnt_c = fr.count("C")
cnt_g = fr.count("G")
cnt_t = fr.count("T")


## 03. Print the Number of Bases

print("%d %d %d %d" %(cnt_a, cnt_c, cnt_g, cnt_t))
```



## Link

> [Counting DNA Nucleotides](http://rosalind.info/problems/dna/)
