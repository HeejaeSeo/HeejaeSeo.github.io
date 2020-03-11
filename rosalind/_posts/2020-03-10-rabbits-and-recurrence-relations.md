# 17. Rabbits and Recurrence Relations

[Question](http://rosalind.info/problems/fib/)


> **Given**    
>  Positive integers n ≤ 40 and k ≤ 5.

> **Return**    
> The total number of rabbit pairs that will be present after n months, 
if we begin with 1 pair and in each generation, every pair of reproduction-age rabbits produces a litter of k rabbit pairs.
(instead of only 1 pair)
 
```python

## 00. Define Function - Fibonacci (Dynamic Programming)

def fibo_dyna(n, k) :

	fibo_new = [0, 0]
	fibo_total = [0, 1]

	if n < 2 :
		return fibo_total[n]

	else :
		for i in range(2, n + 1) :
			fibo_new.append(fibo_total[i - 2] * k)
			fibo_total.append(fibo_total[-1] + fibo_new[-1])

	return fibo_total[n]
  

## 01. Read File

with open("rosalind_fib.txt") as f :
	fr = f.readline()

	n = int(fr.split(" ")[0])
	k = int(fr.split(" ")[1])


## 02. Print Rabbit Pairs

print(fibo_dyna(n, k))

```


## Link

> [Rabbits and Recurrence Relations](http://rosalind.info/problems/fib/)
