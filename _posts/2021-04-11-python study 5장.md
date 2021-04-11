```python
#연습문제 5.1
song="""When an eel grabs your arm,
And it causes great harm,
That;s-a moray!"""

```


```python
song.replace('moray','Moray')
```




    'When an eel grabs your arm,\nAnd it causes great harm,\nThat;s-a Moray!'




```python
#연습문제 5.3
a='roast beef'
b='harm'
c='head'
d='clam'
"My kitty cat likes %s"%a 

```




    'My kitty cat likes roast beef'




```python
"My kitty cat likes %s"%b
```




    'My kitty cat likes harm'




```python
"My kitty cat fell on his %s And now thinks he's a %s"%(c,d)
```




    "My kitty cat fell on his head And now thinks he's a clam"




```python
#연습문제 5.4 , 5.5
a='salutation'
b='name'
c='product'
d='verbed'

"Dear {} {}, Thank you for yout letter. we are sorry that our {} {}".format(a,b,c,d)

```




    'Dear salutation name, Thank you for yout letter. we are sorry that our product verbed'




```python
#연습문제 5.6, 5.7

a='duck'
b='gourd'
c='spitz'

'Ducky Mc{}face'.format(a.capitalize())

```




    'Ducky McDuckface'




```python
'Gourdy Mc{}face'.format(b.capitalize())
```




    'Gourdy McGourdface'




```python
#연습문제 5.8
a='duck'
b='gourd'
c='spitz'

f'Ducky Mc{a.capitalize()}face'
```




    'Ducky McDuckface'




```python

```
