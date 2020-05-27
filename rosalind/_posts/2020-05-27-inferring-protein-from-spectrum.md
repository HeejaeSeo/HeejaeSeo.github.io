# 43. Inferring Protein from Spectrum

* The prefix spectrum of a weighted string is the collection of all its prefix weights.


> **Given**    
>  A list L of n (n ≤ 100) positive real numbers.

> **Return**    
> A protein string of length n−1 whose prefix spectrum is equal to L.  
(if multiple solutions exist, you may output any one of them)
 
```python

## 00. Set Variables

massTable = {
	'A' : 71.03711,
	'C' : 103.00919,
	'D' : 115.02694,
	'E' : 129.04259,
	'F' : 147.06841,
	'G' : 57.02146,
	'H' : 137.05891,
	'I' : 113.08406,
	'K' : 128.09496,
	'L' : 113.08406,
	'M' : 131.04049,
	'N' : 114.04293,
	'P' : 97.05276,
	'Q' : 128.05858,
	'R' : 156.10111,
	'S' : 87.03203,
	'T' : 101.04768,
	'V' : 99.06841,
	'W' : 186.07931,
	'Y' : 163.06333,
}


## 01. Read File

with open("rosalind_spec.txt") as f :
	spec_ls = f.read().strip().split("\n")
  

## 02. Calculate

for i in range(1, len(spec_ls)) :
	wgt = round(float(spec_ls[i]) - float(spec_ls[i - 1]), 5)

	for n, v in massTable.items() :
		if abs(wgt - v) < 0.0001 :
			if n == 'L' :
				continue
			print(n, end = "")

```


## Link

> [Inferring Protein from Spectrum](http://rosalind.info/problems/spec/)
