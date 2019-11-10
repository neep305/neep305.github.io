---
layout: post
title: ijson을 활용한 JSON 파일 
subtitle: 사용법 확인
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,json,parser]
---

### ijson?
Ijson is an iterative JSON parser with a standard Python iterator interface.

### ijson 설치하기
최신 버전(2019.10.22 현재) 2.5.1 설치하기
```bash
$ pip install ijson
```

### 예제
```json
{
  "earth": {
    "europe": [
      {"name": "Paris", "type": "city", "info": { ... }},
      {"name": "Thames", "type": "river", "info": { ... }},
      // ...
    ],
    "america": [
      {"name": "Texas", "type": "state", "info": { ... }},
      // ...
    ]
  }
}
```

```python
import ijson

f = urlopen('http://.../')
objects = ijson.items(f, 'earth.europe.item')
cities = (o for o in objects if o['type'] == 'city')
for city in cities:
  do_something_with(city)
```

사이즈가 큰 json 파일에 prefix를 붙일때에는 Json 오브젝트를 생성해서 쓰지 않는 것이 낫다.
```python
import ijson

parser = ijson.parse(urlopen('http://.../'))
stream.write('<geo>')
for prefix, event, value in parser:
    if (prefix, event) == ('earth', 'map_key'):
        stream.write('<%s>' % value)
        continent = value
    elif prefix.endswith('.name'):
        stream.write('<object name="%s"/>' % value)
    elif (prefix, event) == ('earth.%s' % continent, 'end_map'):
        stream.write('</%s>' % continent)
stream.write('</geo>')
```


