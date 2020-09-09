---
layout: post
title: ColorMapper로 데이터구분해서 보여주기
subtitle: CategoricalColorMapper
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python, bokeh, colormapper, visualization]
---
## Pandas data
```
    mpg  cyl  displ   hp  weight  accel  yr  origin              name  color  \
0  18.0    6  250.0   88    3139   14.5  71      US      ford mustang   blue   
1   9.0    8  304.0  193    4732   18.5  70      US          hi 1200d   blue   
2  36.1    4   91.0   60    1800   16.4  78    Asia  honda civic cvcc    red   
3  18.5    6  250.0   98    3525   19.0  77      US      ford granada   blue   
4  34.3    4   97.0   78    2188   15.8  80  Europe         audi 4000  green   

   size  
0  15.0  
1  20.0  
2  10.0  
3  15.0  
4  10.0
```

## 테스트코드
- 'origin' 컬럼을 legend로 선택
- factors에 legend로 표현할 데이터와 palette 컬러를 매핑
- color에 명시적으로 origin 필드에 대해 color_mapper를 할당

```python
#Import CategoricalColorMapper from bokeh.models
from bokeh.models import CategoricalColorMapper

# Convert df to a ColumnDataSource: source
source = ColumnDataSource(df)

# Make a CategoricalColorMapper object: color_mapper
color_mapper = CategoricalColorMapper(factors=['Europe', 'Asia', 'US'],
                                      palette=['red', 'green', 'blue'])

# Add a circle glyph to the figure p
p.circle('weight', 'mpg', source=source,
            color=dict(field='origin', transform=color_mapper),
            legend='origin')

# Specify the name of the output file and show the result
output_file('colormap.html')
show(p)
```
