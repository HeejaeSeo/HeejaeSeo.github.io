# 06. Translating RNA into Protein

* The 20 commonly occurring amino acids are abbreviated by using 20 letters from the English alphabet.

  (all letters except for B, J, O, U, X, and Z) 

* Protein strings are constructed from these 20 symbols. 

* Henceforth, the term genetic string will incorporate protein strings along with DNA strings and RNA strings.

* The RNA codon table dictates the details regarding the encoding of specific codons into the amino acid alphabet.


> **Given**   
> An RNA string s corresponding to a strand of mRNA (of length at most 10 kbp).

> **Return**   
> The protein string encoded by s.
 
```python

## 00. Define Function

def translate(seq):  

    # Set Variables
    protein = ""

    # Create Codon Table
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
    
    if len(seq) % 3 == 0: 
        for i in range(0, len(seq), 3): 
            codon = seq[i : i + 3] 
            protein += table[codon] 
            
    return protein


## 01. Read File

with open("rosalind_prot.txt", 'r') as f :
    fr = f.readline()
    fr = fr.replace("\n", "")


## 02. Translate RNA into Protein

strand = fr.replace("U", "T")
strand_trans = translate(strand)


## 03. Print Protein String

print(strand_trans)

```


## Link

> [Translating RNA into Protein](http://rosalind.info/problems/prot/)
