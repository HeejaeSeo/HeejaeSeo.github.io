# 18. Mortal Fibonacci Rabbits

* Recall the definition of the Fibonacci numbers from “Rabbits and Recurrence Relations”, 
which followed the recurrence relation Fn = Fn−1 + Fn−2 and assumed that each pair of rabbits reaches maturity 
in one month and produces a single pair of offspring (one male, one female) each subsequent month.

* Our aim is to somehow modify this recurrence relation to achieve a dynamic programming solution 
in the case that all rabbits die out after a fixed number of months.


> **Given**    
>  Positive integers n ≤ 100 and m ≤ 20.

> **Return**    
> The total number of pairs of rabbits that will remain after the n-th month if all rabbits live for m months.
 
```python

## 00. Define Function

def fibo_dyna(n, m) :

	fibo_new = [1, 0]
	fibo_total = [1, 1]

	if n < 2 :
		return fibo_total[n]

	else :
		for i in range(2, n + 1) :
			tmp = 0

			# fibo_new
			for j in range(m - 1) :
				if i >= j + 2 :
					tmp += fibo_new[-(j + 2)]
				else :
					continue

			fibo_new.append(tmp)

			# death
			if i >= m :
				death = fibo_new[i - m]
			else :
				death = 0

			# fibo_total
			fibo_total.append(fibo_total[-1] + fibo_new[-1] - death)

	return fibo_total[n]
  

## 01. Read File

with open("rosalind_fibd.txt") as f :
	fr = f.readline()

	n = int(fr.split(" ")[0])
	m = int(fr.split(" ")[1])


## 02. Print Rabbit Pairs

print(fibo_dyna(n - 1, m))


```


## Link

> [Mortal Fibonacci Rabbits](http://rosalind.info/problems/fibd/)
