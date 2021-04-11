```python

#6.1 for문으로 리스트[3,2,1,0] 출력

list(range(3,-1,-1))
```




    [3, 2, 1, 0]




```python
#6.2
number='3'
guess_me='5'
while True:
    if guess_me>number:
        print('too low')
        break
    if guess_me<number:
        print('oops')
        break
    if guess_me==number:
        print('found it')
        break

```

    too low



```python
#6.3 
guess_me='2'
number='4'
for x in range(10):
    if guess_me>number:
        print('too low')
    if guess_me<number:
        print('oops')
    if guess_me==number:
        print('found it')
```

    oops
    oops
    oops
    oops
    oops
    oops
    oops
    oops
    oops
    oops



```python

```


```python

```
