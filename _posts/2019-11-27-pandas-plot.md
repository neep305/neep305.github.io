---
layout: post
title: Pandas DataFrame와 Matplotlib 활용한 데이터차트 그리기
subtitle: pyplot 사용하여 데이터 시각화하기
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,pandas,matplotlib,pyplot,scatterplot,barplot]
---

# Making a DataFrame
> 샘플데이터를 DataFrame 형태로 가공한다.

```python
# http://queirozf.com/entries/pandas-dataframe-plot-examples-with-matplotlib-pyplot
import pandas as pd

df = pd.DataFrame({
    'name':['john','mary','peter','jeff','bill','lisa','jose'],
    'age':[23,78,22,19,45,33,20],
    'gender':['M','F','M','M','M','F','M'],
    'state':['california','dc','california','dc','california','texas','texas'],
    'num_children':[2,0,0,3,2,1,4],
    'num_pets':[5,1,0,5,2,2,3]
})

print(df)
```

# Choose two columns to make a scatter plot

```python
import matplotlib.pyplot as plt
import pandas as pd

# a scatter plot comparing num_children and num_pets
df.plot(kind='scatter',x='num_children',y='num_pets',color='red')
plt.show()
```

# Choose two columns to make a bar plot
```python
import matplotlib.pyplot as plt
import pandas as pd

# a simple line plot
df.plot(kind='bar',x='name',y='age')
```

# Making a line plot
```python
import matplotlib.pyplot as plt
import pandas as pd

# gca stands for 'get current axis'
ax = plt.gca()

df.plot(kind='line',x='name',y='num_children',ax=ax)
df.plot(kind='line',x='name',y='num_pets', color='red', ax=ax)

plt.show()
```

# Save a graph

```python
import matplotlib.pyplot as plt
import pandas as pd

df.plot(kind='bar',x='name',y='age')

# the plot gets saved to 'output.png'
plt.savefig('output.png')
```

# Bar plot with 'group by'

```python
import matplotlib.pyplot as plt
import pandas as pd

df.plot(kind='bar',x='name',y='age')

# the plot gets saved to 'output.png'
plt.savefig('output.png')
```