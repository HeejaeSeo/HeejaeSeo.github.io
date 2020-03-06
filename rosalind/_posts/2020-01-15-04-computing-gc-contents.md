# 04. Computing GC Contents

The GC-content of a DNA string is given by the percentage of symbols in the string that are 'C' or 'G'. 

(ex. GC-content of "AGCTATAG" = 37.5%)

Note that the reverse complement of any DNA string has the same GC-content.


> **Given**
> > At most 10 DNA strings in FASTA format (of length at most 1 kbp each).

> **Return**
> > The ID of the string having the highest GC-content, followed by the GC-content of that string.
 
```python

## 01. Set Variables

data = [0, 0, 1, 0]  # data = [id, number of 'C', number of 'G', GC content]
best = ['name', 0]   # best = [id, GC content] of highest GC content String 

cnt_c = cnt_g = 0


## 02. Calculate GC Contents of Each String 

with open('rosalind_gc.txt', 'r') as f :
    for s in f :      
        if s.startswith(">") :
            data[3] = data[1]/data[2] * 100
            print(data)

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
print(data)

if data[3] > best[1] :
    best[0] = data[0]
    best[1] = data[3]


## 03. Print the Highest GC Content String

print(best[0])
print(best[1])
```

## Result

~~~
['>Rosalind_7682\n', 416, 834, 49.88009592326139]
['>Rosalind_4087\n', 460, 918, 50.108932461873636]
['>Rosalind_0953\n', 469, 941, 49.840595111583426]
['>Rosalind_3776\n', 417, 841, 49.58382877526754]
['>Rosalind_6442\n', 479, 928, 51.616379310344826]
['>Rosalind_6761\n', 504, 994, 50.70422535211267]
['>Rosalind_4469\n', 480, 913, 52.573932092004384]
['>Rosalind_7918\n', 403, 836, 48.20574162679426]
['>Rosalind_4663\n', 457, 959, 47.653806047966626]
['>Rosalind_4687\n', 396, 803, 49.31506849315068]

>Rosalind_4469
52.573932092004384
~~~

## Answer

~~~
>Rosalind_4469
52.573932092004384
~~~


## Link

> [Computing GC Content](http://rosalind.info/problems/gc/)
