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
