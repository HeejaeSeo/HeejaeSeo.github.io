# 29. Partial Permutations

* A partial permutation is an ordering of only k objects taken from a collection containing n objects (i.e. k ≤ n).

* For example, one partial permutation of three of the first eight positive integers is given by (5, 7, 2).

* The statistic P(n, k)counts the total number of partial permutations of k objects that can be formed from a collection of n objects.


> **Given**    
> Positive integers n and k such that 100 ≥ n > 0 and 10 ≥ k > 0.

> **Return**    
> The total number of partial permutations P(n, k), modulo 1,000,000.
 
```python

## 00. Set Variables

result = 1


## 01. Read File

with open("rosalind_pper.txt") as f :
	fr = f.readline()
	fr = fr.replace("\n", "")

	n = int(fr.split(" ")[0])
	k = int(fr.split(" ")[1])


## 02. Get the Number of Permutations

for i in range(k) :
	result *= n
	result %= 1000000
	n -= 1

print(result)

```


## Link

> [Partial Permutations](http://rosalind.info/problems/pper)
