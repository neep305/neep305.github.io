---
layout: post
title: Stacked/Unstacked 사용하여 데이터 재구조화하기
subtitle: pd.DataFrame.stack(), pd.DataFrame.unstack()
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,stacked,unstacked,multi-index]
---

### Stacked? Unstacked?
> Stacked(long), Unstacked(wide)

```python
import numpy as np
import pandas as pd


def stacked():
    mul_index = pd.MultiIndex.from_tuples([('cust1','2015'),('cust1','2016'),('cust2','2015'),('cust2','2016')])

    data = pd.DataFrame(data=np.arange(16).reshape(4,4),
                        index=mul_index,
                        columns=['prd_1','prd_2','prd_3','prd_4'],
                        dtype='int')

    print(data)
    # 결과
    #               prd1    prd2    prd3    prd4
    # cust1 2015    0       1       2       3
    #       2016    4       5       6       7
    # cust2 2015    8       9       10      11
    #       2016    12      13      14      15
    return data

if __name__ == '__main__':
    data_stack = stacked().stack()
    print(data_stack)
```