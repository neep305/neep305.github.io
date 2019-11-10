---
layout: post
title: high order function이란?
subtitle: filter, exclude
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,high-order-function,lambda]
---

### What is 'High order function'
#### from Wikipedia
```
In mathematics and computer science, a higher-order function is a function that does at least one of the following:

takes one or more functions as arguments (i.e. procedural parameters),
returns a function as its result.
All other functions are first-order functions. In mathematics higher-order functions are also termed operators or functionals. The differential operator in calculus is a common example, since it maps a function to its derivative, also a function. Higher-order functions should not be confused with other uses of the word "functor" throughout mathematics, see Functor (disambiguation).
```

#### Sample 
> javascript
```javascript
const twice = (f, v) => f(f(v));
const add3 = v => v + 3;

twice(add3, 7); // 13
```

> python
```python
def twice(f):
    def result(a):
        return f(f(a))
    return result

plusthree = lambda x: x+3

g = twice(plusthree)
    
g(7)
>>> 13
```