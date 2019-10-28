---
layout: post
title: django filter 사용하기
subtitle: filter, exclude
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,django,filter]
---

### 특정 오브젝트를 필터를 사용하여 추출하기(Retrieving specific objects with filters)

#### filter
```python
Entry.objects.filter(pub_date__year=2006)
```

#### exclude
```python
q = Entry.objects.filter(headline__startswith="What")
q = q.filter(pub_date__lte=datetime.date.today())
q = q.exclude(body_text__icontains="food")
```

#### 필터 체이닝
```python
Entry.objects.filter(headline__startswith='What').exclude(pub_date__gte=datetime.date.today()
).filter(pub_date__gte=datetime.date(2005, 1, 30))
```