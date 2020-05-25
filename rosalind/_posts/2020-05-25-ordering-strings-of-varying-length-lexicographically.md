# 42. Ordering Strings of Varying Length Lexicographically

* Say that we have strings s = s1 s2 ⋯ sm and t = t1 t2 ⋯ tn with m<n. 

* Consider the substring t′ = t[1 : m]. 

> **Given**    
> A permutation of at most 12 symbols defining an ordered alphabet 𝒜 and a positive integer n (n ≤ 4).

> **Return**    
> All strings of length at most n formed from 𝒜, ordered lexicographically.   
(Note : As in “Enumerating k-mers Lexicographically”, 
alphabet order is based on the order in which the symbols are given.)
 
```python

## 00. Set Variables

total_ls = []
seq = ""


## 01. Define Function

def lex(seq, cnt) :

	if cnt > 0 :
		for i in range(length) :
			tmp = seq
			tmp += string[i]
			print(tmp)
			lex(tmp, cnt - 1)
	else :
		return(seq)


## 02. Read File

with open("rosalind_lexv.txt") as f :
	fr = f.read().strip().split("\n")

string = fr[0].split(" ")
num = int(fr[1])
length = len(string)


## 03. Call the Function

lex(seq, num)

```


## Link

> [Ordering Strings of Varying Length Lexicographically](http://rosalind.info/problems/lexv/)
