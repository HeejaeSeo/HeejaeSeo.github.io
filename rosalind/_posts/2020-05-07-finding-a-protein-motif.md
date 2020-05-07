# 41. Finding a Protein Motif

[Question](http://rosalind.info/problems/mprt)


> **Given**    
> At most 15 UniProt Protein Database access IDs.

> **Return**    
> For each protein possessing the N-glycosylation motif, 
output its given access ID followed by a list of locations in the protein string where the motif can be found.
 
```python

## 00. Import Library

import requests
import re


## 01. Set Variables

prot_ls = []


## 02. Read File

with open("rosalind_mprt.txt") as f :
	prot_ls = f.read().strip().split("\n")
  

## 03. Find Motifs of Proteins

for protId in prot_ls :
	tmp_ls = []

	# Request FASTA File
	res = requests.get("http://www.uniprot.org/uniprot/%s.fasta" %protId)

	# Extract Protein Code from FASTA File
	fasta = res.text
	start = fasta.find("\n")
	protein = fasta[(start + 1) :].replace("\n", "")

	# Find N-glycosylation Motif
	motif = re.finditer("(?=(N[^P][ST][^P]))", protein)

	# Get the Locations of Each Motif
	for x in motif :
		tmp_ls.append(x.start() + 1)

	# Print ProteinID & Locations of Motifs
	if tmp_ls :
		print(protId)

		for x in tmp_ls :
			print(x, end = " ")
		print()


```


## Link

> [Finding a Protein Motif](http://rosalind.info/problems/mprt)

> [Reference](https://recologia.com.br/2015/07/rosalind-finding-a-protein-motif/)

