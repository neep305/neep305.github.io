---
layout: post
title: Calculating lift & significance testing
subtitle: AB Test 결과 분석
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,abtest,lift,significance]
---

# Formula
**Calculating lift**

$$
Calculating\_lift = \frac{Treadment\_conversion\_rate - Control\_conversion\_rate}{Control\_conversion\_rate} 
$$

# Code

```python
# Calculate the mean of a and b
a_mean = np.mean(control)
b_mean = np.mean(personalization)

# Calculating the lift using a_mean and b_mean
lift = (b_mean-a_mean) / a_mean

print("lift: ", str(round(lift*100,2)) + '%')
```

# T-분포(distribution), T-검정(T-test) & P-value
## [T-distribution](http://godrag77.blogspot.com/2011/07/t-students-t-distribution.html)이란?

> 모평균과 모표준편차를 모르는 정규모집단에서 표본크기가 작은 경우에 모평균에 대한 추정과 검정을 할 경우 t 통계량을 이용하는데 정규모집단으로 부터 크기 n인 표본을 무작위로 추출했을 때 표본통계량 t는 자유도 (n-1)인 t 분포를 따른다.


## 자유도
> 자유도 : 표본분포(sampling distribution)를 구성하기 위해 자유롭게 반복해서 추출할 수 있는 표본(repeated random

## T-test
> Code

```python
from scipy.stats import ttest_ind

t = ttest_ind(control, personalized)

print(t)
```

## P-value
- T-statistic of 1.96 is typically statistically significant at the 95% level
- Depending on the context of the test, you may be comfortable with a lower or higher level of statistical significance
