# 15. Open Reading Frames

* Either strand of a DNA double helix can serve as the coding strand for RNA transcription. 

* Hence, a given DNA string implies six total reading frames, or ways in which the same region of DNA can be translated into amino acids.

* Three reading frames result from reading the string itself, whereas three more result from reading its reverse complement.

* An open reading frame (ORF) is one which starts from the start codon and ends by stop codon, without any other stop codons in between. 

* Thus, a candidate protein string is derived by translating an open reading frame into amino acids until a stop codon is reached.


> **Given**    
> A DNA string s of length at most 1 kbp in FASTA format.

> **Return**    
> Every distinct candidate protein string that can be translated from ORFs of s.   
Strings can be returned in any order.
 
```python

## 00. Set Variables

seq = ""
seq_rev_com = ""
prot_ls = []


## 01. Define Functions

# 01. Translate into Protein
def translate(seq):  
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

	protein = ""

	for i in range(0, len(seq), 3): 

		if i + 2 < len(seq) :
			codon = seq[i : i + 3]

			if table[codon] == "_" :
				return protein
			else :
				protein += table[codon]
		else :
			break

# 02. Create Complementary String
def comp(seq) :
	string_new = ''

	for i in seq :

		if i == 'A' :
			string_new += 'T'
		elif i == 'T' :
			string_new += 'A'
		elif i == 'G' :
			string_new += 'C'
		else :
			string_new += 'G'

	return string_new

# 03. Synthesis
def synthesis(string) :
	for i in range(len(string) - 2) :
		if string[i : i + 3] == "ATG" :
			protein = translate(string[i :])
			if protein != None :
				prot_ls.append(protein)


## 02. Read File

with open("rosalind_orf.txt", 'r') as f :
	fr = f.readlines()

for i in range(len(fr)) :
	fr[i] = fr[i].replace("\n", "")


## 03. Connect String

for i in range(1, len(fr)) :
	seq += fr[i]

seq_rev = seq[::-1]
seq_com = comp(seq)
seq_rev_com = comp(seq_rev)


## 04. Translate Protein Sequences

synthesis(seq)
synthesis(seq_rev_com)

# Sorting is Optional
prot_ls = list(set(prot_ls))
prot_ls = sorted(prot_ls)


## 05. Print Proteins

for x in prot_ls :
	print(x)

```


## Link

> [Open Reading Frames](http://rosalind.info/problems/orf/)
