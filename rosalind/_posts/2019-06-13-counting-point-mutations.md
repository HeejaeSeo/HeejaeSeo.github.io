# 05. Counting Point Mutations

* Given two strings s and t of equal length, the Hamming distance between s and t denoted dH(s,t), is the number of corresponding symbols that differ in s and t.


> **Given**   
>  Two DNA strings s and t of equal length (not exceeding 1 kbp).

> **Return**   
> The Hamming distance. 
 
```python

## 00. Set Variables

num = 0


## 01. Read File

with open("rosalind_hamm.txt") as f :
	fr = f.readlines()
	
s = fr[0].replace("\n", "")
t = fr[1].replace("\n", "")


## 02. Count the Number of Point Mutations 

length = len(s)

for i in range(length) :
	if (s[i] == t[i]) :
		continue
	else :
		num += 1
    
    
## 03. Print the Number of Mutations

print(num)

```



## Link

> [Counting Point Mutations](http://rosalind.info/problems/hamm/)
