---
layout: post
title: [Python] How to use lambda
subtitle: 람다 function 사용하기
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,lambda,anonymous function]
---

### Expression
Lambda 예제
```python
# lambda arguments : expression

# example 1
x = lambda a : a + 10
print(x(5))

x = lambda a,b : a * b
print(x(3,5))

x = lambda a,b,c : a + b + c
print(x(1,2,3))
```

Lamdbda function을 사용하는 이유
- Lambda의 강점은 다른 function 내에서 익명함수를 쓸 수 있다는 점이다.
```python
def getSome(a):
  return lambda a : a * n
  
getAny = getSome(5)

print(getAny(11)
```
> 결과값 : 55

### Syntax
> No Statements
A lambda function can’t contain any statements.
```python
>>> (lambda x: assert x == 2)(2)
  File "<input>", line 1
    (lambda x: assert x == 2)(2)
                    ^
SyntaxError: invalid syntax
```

> Single Expression
```python
>>> (lambda x:
... (x % 2 and 'odd' or 'even'))(3)
'odd'
```

#### Type Annotation
> 함수에서 사용하는 Type hint를 Lambda에서는 사용할 수 없다.

```python
# function
def full_name(first: str, last: str) -> str:
    return f'{first.title()} {last.title()}'
```
```python
# lambda function
>>> lambda first: str, last: str: first.title() + " " + last.title() -> str
  File "<stdin>", line 1
    lambda first: str, last: str: first.title() + " " + last.title() -> str

SyntaxError: invalid syntax
```

#### IIFE(Immediately Invoked Function Execution)
- Lambda에 값을 대입하여 바로 함수를 실행하도록 할 수 있다.
```python
result = (lambda x: x * x)(4)
print(result) # result = 16
```