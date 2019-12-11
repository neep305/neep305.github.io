---
layout: post
title: Python Generator
subtitle: advantages using generator
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,generator,iterator]
---

# Python Generator? 
> [wikidocs.net](https://wikidocs.net/16069)에서 발췌하였습니다.

- generator : iterator를 생성해주는 함수, 함수안에 yield 키워드를 사용함
- genrator 특징
    - iterable한 순서가 지정됨(모든 generator는 iterator)
    - 느슨하게 평가된다.(순서의 다음 값은 필요에 따라 계산됨)
    - 함수의 내부 로컬 변수를 통해 내부상태가 유지된다.
    - 무한한 순서가 있는 객체를 모델링할 수 있다.(명확한 끝이 없는 데이터 스트림)
    - 자연스러운 스트림 처리를 위 파이프라인으로 구성할수 있다.(Java에서 파일스트림 처리시에 특정 바이트단위로 반복하는 것을 말하는듯..)

## yield
> yield는 python 3.3 이후부터 사용 가능

```python
result = [x**2 for in range(4)]
print(result)
# 결과값 [0,1,4,9] 

# 위 loop를 generator로 만들려면 ()로 결과값을 묶어주면 된다.
result = (x**2 for in range(4))
print(type(result))

def get_result(result_arr)
    for i in result_arr:
        yield i

# yield가 호출되면 암시적으로 return이 호출된다.
print(next(get_result(result))) # 결과값 0

# list로 변환해서 출력하기
print(list(get_result(result))) # 결과값 [0,1,4,9]

# 만약에 결과값을 변수에 할당 후 위의 출력을 실행하면 결과가 다르게 나온다.
result_get = get_result(result)

print(next(result_get)) # 결과값 0

print(list(result_get)) # 결과값 [1,4,9]
```