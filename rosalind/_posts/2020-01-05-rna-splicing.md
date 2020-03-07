# 09. RNA Splicing

* After identifying the exons and introns of an RNA string, 
we only need to delete the introns and concatenate the exons to form a new string ready for translation.


> **Given**  
A DNA string s (of length at most 1 kbp) and a collection of substrings of s acting as introns.   
All strings are given in FASTA format.

> **Return**  
> A protein string resulting from transcribing and translating the exons of s.   
(Note : Only one solution will exist for the dataset provided.)
 
```python

## 00. Set Variables

cnt = 1
seq_dna = ""
intron_ls = []


## 01. Define Function - Convert DNA into Protein

def Translate(seq) :
	length = len(seq)
	protein = ""

	## Translate Table
	table = { 
		'ATA':'I', 'ATC':'I', 'ATT':'I', 'ATG':'M',
		'ACA':'T', 'ACC':'T', 'ACG':'T', 'ACT':'T',
		'AAC':'N', 'AAT':'N', 'AAA':'K', 'AAG':'K',
		'AGC':'S', 'AGT':'S', 'AGA':'R', 'AGG':'R',
		'CTA':'L', 'CTC':'L', 'CTG':'L', 'CTT':'L',
		'CCA':'P', 'CCC':'P', 'CCG':'P', 'CCT':'P',
		'CAC':'H', 'CAT':'H', 'CAA':'Q', 'CAG':'Q',
		'CGA':'R', 'CGC':'R', 'CGG':'R', 'CGT':'R',
		'GTA':'V', 'GTC':'V', 'GTG':'V', 'GTT':'V',
		'GCA':'A', 'GCC':'A', 'GCG':'A', 'GCT':'A',
		'GAC':'D', 'GAT':'D', 'GAA':'E', 'GAG':'E',
		'GGA':'G', 'GGC':'G', 'GGG':'G', 'GGT':'G',
		'TCA':'S', 'TCC':'S', 'TCG':'S', 'TCT':'S',
		'TTC':'F', 'TTT':'F', 'TTA':'L', 'TTG':'L',
		'TAC':'Y', 'TAT':'Y', 'TAA':'_', 'TAG':'_',
		'TGC':'C', 'TGT':'C', 'TGA':'_', 'TGG':'W'
	}

	for i in range(0, length, 3) :
		codon = seq[i : i + 3]
		if table[codon] == "_" :
			break
		else :
			protein += table[codon]

	return protein

## 02. Read File

with open("rosalind_splc.txt", 'r') as f :
	fr = f.readlines()

	for i in range(len(fr)) :
		fr[i] = fr[i].replace("\n", "")


## 03. Designate Sequence

for i in range(len(fr)) :
	if fr[i].startswith(">") == 0 :
		if fr[i - 1].startswith(">") == 0 :
			seq_dna += fr[i]
		else :
			intron_ls.append(fr[i])
      
# Delete 1st Element
seq_dna = intron_ls[0] + seq_dna
intron_ls.pop(0)


## 04. Remove Introns
for seq in intron_ls :
	if seq in seq_dna :
		seq_dna = seq_dna.replace(seq, "")
    
    
## 05. Translate & Print
protein = Translate(seq_dna)
print(protein)

```


## Link

> [RNA Splicing](http://rosalind.info/problems/splc/)
