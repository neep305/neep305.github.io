---
layout: post
title: Pandas를 이용한 JSON 파일을 Table 형식 정제
subtitle: JSON to CSV
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [pandas,python,json,dataframe]
---

### Get JSON file
> Get JSON file to manipulate
[result.json](../_samples/result.csv)

### Import

~~~python
import pandas as pd
import json
~~~

### Read JSON file
```python
with open('result.json', encoding='utf-8', mode='r') as f:
  array = json.load(f)
```

### Get array and put it into DataFrame
```python
data = array[0]
df = pd.DataFrame.from_dict(data, orient='columns')
```

### Arrange column order and give new column names
```python
df_arrange = pd.DataFrame(df, columns=['prdNm','prdCost','isFavorite','soldCnt','url','imgUrl'])
col_dict = {"prdNm":"상품명","prdCost":"판매가","isFavorite":"Favorite배지","soldCnt":"판매건수","url":"상품링크","imgUrl":"이미지링크"}
df_kr_col = df_arrange.rename(col_dict, axis=1)
```

### Extract file to excel
```python
df_kr_col.to_excel('result_new.xlsx)
```