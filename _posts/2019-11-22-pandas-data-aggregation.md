---
layout: post
title: Pandas Aggregation
subtitle: groupby()
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [pandas,python,groupby]
---

### groupby()
> Pandas는 groupby 메소드를 이용하여, Series(1차원) 또는 DataFrame(n차원)의 데이터 그룹핑을 할 수 있다.

```python
df = pd.DataFrame({'Animal': ['Falcon', 'Falcon','Parrot','Parrot'],'Max Speed': [380., 370., 24., 26.]})

>>> df
   Animal  Max Speed
0  Falcon      380.0
1  Falcon      370.0
2  Parrot       24.0
3  Parrot       26.0

>>> df.groupby(['Animal']).mean()
        Max Speed
Animal
Falcon      375.0
Parrot       25.0
```

> Groupby 조건 설정
- by: 그룹핑할 특정 컬럼 지정
- axis: 0은 열(column) 단위, 1은 행(index) 단위
- as_index: 별도의 인덱스로 만들지 말지

```python
sub_data_grp = sub_data_demo.groupby(by = ['country','device'], axis=0, as_index=False)

sub_data_grp
```