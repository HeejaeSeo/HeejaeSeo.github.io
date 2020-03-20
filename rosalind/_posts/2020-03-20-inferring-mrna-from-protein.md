# 24. Inferring mRNA from Protein

* For positive integers a and n, a modulo n(written a mod n in shorthand) is the remainder when a is divided by n.  

* Modular arithmetic is the study of addition, subtraction, multiplication, and division with respect to the modulo operation.

* We say that a and b are congruent modulo n if a mod n = b mod n; in this case, we use the notation a≡b modn.


> **Given**    
> A protein string of length at most 1000 aa.

> **Return**    
> The total number of different RNA strings from which the protein could have been translated, modulo 1,000,000.   
(Don't neglect the importance of the stop codon in protein translation.)
 
```python

## 00. Set Variables

string = ""
result = 3  # setting result as the number of stop codon in advance
codon_dic = {
	"F" : 2, "L" : 6, "S" : 6, "Y" : 2, "C" : 2, "W" : 1, "P" : 4, 
	"H" : 2, "Q" : 2, "R" : 6, "I" : 3, "M" : 1, "T" : 4, "N" : 2, 
	"K" : 2, "V" : 4, "A" : 4, "D" : 2, "E" : 2, "G" : 4
	}


## 01. Read File

with open("rosalind_mrna.txt") as f :
	fr = f.readlines()

	for i in range(len(fr)) :
		fr[i] = fr[i].replace("\n", "")
		string += fr[i]


## 02. Reverse Translate

for i in range(len(string)) :
	result *= codon_dic[string[i]]
	result = result % 1000000


## 03. Print Answer

print(answer)

```


## Link

> [Inferring mRNA from Protein](http://rosalind.info/problems/mrna/)
