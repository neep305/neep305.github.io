---
layout: post
title: %timeit로 range() 퍼포먼스 비교하기
subtitle: for문과 unpack 비교
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python, performance, jupyternotebook]
---

## 테스트코드

> 아래 코드는 jupyter notebook에서 실행한다.

```python
%timeit [num for num in range(51)]

# 결과
# 2.81 us +- 186 ns per loop (mean +- std. dev. of 7 runs, 100000 loops each)
```

```python
%timeit [*range(51)]

# 결과
# 535 ns +- 87.7 ns per loop (mean +- std. dev. of 7 runs, 1000000 loops each)
```
