---
layout: post
title: 이동평균 구하기
subtitle: using rolling
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,rolling,movingaverage]
---

# 이동평균
- python document link: [이동평균](https://www.openaitrading.com/python-pandas-%EC%9D%B4%EB%8F%99%ED%8F%89%EA%B7%A0-%EA%B5%AC%ED%95%98%EA%B8%B0/)

## 단순이동평균 구하기
```python
moving_avg_10 = data.rolling(10).mean()
moving_avg_20 = data.rolling(20).mean()
```

## 선형 가중 이동평균 구하기
- 각 값별 가중치를 선형으로 주고 이동평균을 계산하는 방법.
- 별도의 선형가중 이동평균 구하는 방법은 없음

## 지수 이동평균(Exponential Moving Average) 구하기
- ewm 활용: 이동평균 프레임수는 span 변수에 할당한다.

```python
e_mov_avg_5 = data.ewm(span=5).mean()
e_mov_avg_10 = data.ewm(span=10).mean()
```

## 이동평균 비교
