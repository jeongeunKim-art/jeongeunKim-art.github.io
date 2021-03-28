# ch3. 숫자


```python
x=5
y=x+12
y
```




    17




```python
two=deux=zwei=2
```


```python
two
```




    2




```python
deux
```




    2




```python
zwei
```




    2




```python
x=5
x
```




    5




```python
y=x
y
```




    5




```python
a=95
a+=2
a
```




    97




```python
#ch3-연습문제(p.93)
a=60
a*=60
a
second_per_hour=a
```


```python
b=3600
b*=24
b
second_per_day=b

```


```python
second_per_day/second_per_hour
```




    24.0




```python
second_per_day//second_per_hour
```




    24



# ch4. 선택하기 :if


```python
disaster=True
if disaster:
    print("woe")
else:
    print("wee")
```

    woe



```python
furry=True
large=False
if furry:
    if large:
        print("a")
    else:
        print("b")
        
else:
    if large:
        print("c")
    else:
        print("d")
```

    b



```python
vowels='aeiou'
letter='o'
letter in vowels
```




    True




```python
if letter in vowels:
    print(letter, 'is a vowel')
    
```

    o is a vowel



```python
#ch4 연습문제-1(p.105) 1-10 사이의 숫자를 선택해서 secret 변수에 할당한다. 그리고 1-10사이의 다른 숫자를 선택해서 guess변수에 할당한다. 
#if, elif, else문을 사용하여 guess 변수가 secret변수보다 작으면 'too law', 크면 'too high', 일치하면 'just right'출력하자
secret='8'
guess='7'

if (secret>guess):
    print('too low')
elif (secret<guess):
    print('too high')
elif (secret==guess):
    print('just right')
```

    too low



```python
#ch4 연습문제-2(p.105) #중첩문 사용함..
small=False
green=False
if small:
    if green:
        print("완두콩은 작고 녹색이다")
    else:
        print("체리는 작고 녹색이 아니다")
        
elif green:
    if small:
        print("수박은 크고 녹색이다")
else:
    print("호박은 크고 녹색이 아니다")
                
```

    호박은 크고 녹색이 아니다



```python

```


```python

```
