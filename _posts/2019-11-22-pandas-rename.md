---
layout: post
title: Pandas Rename 사용하기 
subtitle: index(행), column(열) 이름 변경
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,rename,dataframe]
---

### df.rename()
> index(행), column(열)의 이름을 변경할 때, rename()을 사용한다.

```python
# 예를 들어, 같은 경로에 있는 data.csv파일을 변경한다고 가정해보자.
import pandas as pd

df_data = pd.read_csv('data.csv')

# 열 변환
df_data = df_data.rename({"name":"이름","department":"부서","salary":"연봉"}, axis=1)

# 행 변환
df_data = df_data.rename({0:"zero",10:"ten", axis=0})

# 확인
df_data
```