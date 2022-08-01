---
layout: post
title: Python Enumerate() 사용하기
subtitle: 배열 인덱스 활용
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,generator,iterator]
---

# Enumerate 정의하기

## [Enumerate() in Python](https://www.geeksforgeeks.org/enumerate-in-python/)
> Enumerate() method adds a counter to an iterable and returns it in a form of enumerate object. This enumerate object can then be used directly in for loops or be converted into a list of tuples using list() method. For more information click [here](https://www.scaler.com/topics/enumerate-in-python/).
## 사용해보기

```python
avengers = ['hawkeye', 'ironman', 'thor', 'captain america']
e = enumerate(avengers)
print(type(e)) # <class 'enumerate'>

e_list = list(e)
print(e_list)
[(0,'hawkeye'),(1,'ironman'),(2,'thor'),(3,'captain america')]
```


## Don't write this vs. Write this

```python
# Don't write this
my_container = ['Jason','Mike','Tim']
index = 0
for element in my_container:
    print('{} {}'.format(index, element))
    index++

# Write this
for index, element in enumerate(my_container):
    print('{} {}'.format(index, element))
```
