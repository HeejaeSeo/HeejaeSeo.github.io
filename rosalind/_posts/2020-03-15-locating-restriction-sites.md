# 20. Locating Restriction Sites

* A DNA string is a reverse palindrome if it is equal to its reverse complement. 

* For instance, GCATGC is a reverse palindrome because its reverse complement is GCATGC.


> **Given**    
> A DNA string of length at most 1 kbp in FASTA format.

> **Return**    
> The position and length of every reverse palindrome in the string having length between 4 and 12.   
You may return these pairs in any order.
 
```python

## 00. Set Variables

string = ""
dic = {"A" : "T", "T" : "A", "C" : "G", "G" : "C"}


## 01. Define Function

def isPalindrome(i, k) :
	# dic = {"A" : "T", "T" : "A", "C" : "G", "G" : "C"}
	n = 0
	while(n * 2 < k) :
		if(dic[string[i + n]] == string[i + k - n]) :
			n += 1
		else :
			return False
			break
	return True


## 02. Read File

with open("rosalind_revp.txt") as f :
	fr = f.readlines()

	for i in range(len(fr)) :
			if fr[i].startswith(">") == 0 :

				fr[i] = fr[i].replace("\n", "")
				string += fr[i]


## 03. Find Palindrome Position & Length

for k in range(3, 12, 2) :
	for i in range(len(string) - k) :
		if isPalindrome(i, k) == True :
			print(i + 1, k + 1)
```


## Link

> [Locating Restriction Sites](http://rosalind.info/problems/revp/)
