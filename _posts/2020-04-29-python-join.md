---
layout: post
title: Python join 함수 사용
subtitle: split string, tuple, array, dictionary 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python, join, split]
---

# Getting started
The join() method is a string method and returns a string in which the elements of sequence have been joined by str separator.

## 예제
### 튜플(Tuple)
```
venom = ('Knull','Toxin','Carnage')
extract = '|'.join(venom)

# result
# Knull|Toxin|Carnage
```

### 배열(Array)
```
DC = ['Wonderwoman','Aquaman','Batman','Superman']
movies = '||'.join(DC)

# result: 'Wonderwoman||Aquaman||Batman||Superman'
```

### 딕셔너리(Dictionary)
```
trends = {
    1: 'AI',
    2: 'ML',
    3: 'Serverless',
    4: 'ARVR'
}

picks = '/'.join(trends)

# result: 'AI/ML/Serverless/ARVR'
```