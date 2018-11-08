---
layout: post
title: How to use pandas query
subtitle: Example of pandas query
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [pandas,query]
---

## Pandas Query Document 
You can see examples [pandas query](https://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-query) here.

```python
# For example geting data of specific category (cat_id) in csv file.
import pandas as pd
df_prd = pd.read_csv('./best_prd_20181025.csv')
df_prd[df_prd.cat_id == 50000193]
```
