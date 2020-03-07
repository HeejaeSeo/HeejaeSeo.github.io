# 03. Complementing a Strand of DNA

In DNA strings, symbols 'A' and 'T' are complements of each other, as are 'C' and 'G'.

The reverse complement of a DNA string s is the string formed by reversing the symbols of s,
then taking the complement of each symbol 


> **Given**
> A DNA string s of length at most 1000 bp.

> **Return**
> The reverse complement.
 
```python

## 00. Set Variables

strand_rev = ''
strand_new = ''


## 01. Read File

with open("rosalind_revc.txt") as f :
	fr = f.readline()
	strand = fr.replace("\n", "")


## 02. Create a Reverse Strand

for i in strand :
    strand_rev = i + strand_rev
    
    
## 03. Create a Complementary Strand

for i in strand_rev :
    if i == 'A' :
        strand_new += 'T'
    elif i == 'T' :
        strand_new += 'A'
    elif i == 'G' :
        strand_new += 'C'
    else :
        strand_new += 'G'


## 04. Print New Strand

print(strand_new)

```


## Link

> [Complementing a Strand of DNA](http://rosalind.info/problems/revc/)
