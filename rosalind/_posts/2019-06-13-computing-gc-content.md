# 04. Computing GC Content

* The GC-content of a DNA string is given by the percentage of symbols in the string that are 'C' or 'G'. 

  (ex. GC-content of "AGCTATAG" = 37.5%)

* Note that the reverse complement of any DNA string has the same GC-content.


> **Given**   
> At most 10 DNA strings in FASTA format (of length at most 1 kbp each).

> **Return**   
> The ID of the string having the highest GC-content, followed by the GC-content of that string.
 
```python

## 00. Set Variables

data = [0, 0, 1, 0]  # data = [id, number of 'C', number of 'G', GC content]
best = ['name', 0]   # best = [id, GC content] of highest GC content String 

cnt_c = cnt_g = 0


## 01. Calculate GC Content of Each String 

with open('rosalind_gc.txt', 'r') as f :
    for s in f :      
        if s.startswith(">") :
            data[3] = data[1]/data[2] * 100
            #print(data)

            # Select the highst GC content String
            if data[3] > best[1] :
                best[0] = data[0]
                best[1] = data[3]
                
            data[0] = s
            data[1] = 0
            data[2] = 0
            cnt_c = cnt_g = 0

        else :
            cnt_c = s.count("C")
            cnt_g = s.count("G")
            data[1] = data[1] + cnt_c + cnt_g
            data[2] += len(s.rstrip('\n'))
           

data[3] = data[1]/data[2] * 100

#print(data)

if data[3] > best[1] :
    best[0] = data[0]
    best[1] = data[3]


## 02. Print the Highest GC Content String

print(best[0])
print(best[1])
```


## Link

> [Computing GC Content](http://rosalind.info/problems/gc/)
