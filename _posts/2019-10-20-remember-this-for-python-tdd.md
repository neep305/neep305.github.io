---
layout: post
title: Python Django 개발시 기능테스트
subtitle: 기능테스트가 뭐지?
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,django,tdd,기능테스트,unittests,webdriver,selenium]
---

### 유용한 TDD 개념
- **User Story** : 사용자 관점에서 어떻게 어플리케이션이 동작해야 하는지 기술한 것
- **Expected failure**: 의도적으로 구현한 테스트 실패

### 단위테스트와 기능테스트의 차이점
> 차이점
1) 기능테스트 : 사용자 관점에서 애플리케이션 외부를 테스트하는 것
2) 단위테스트 : 프로그래머 관점에서 내부를 테스트하는 것

### Django 테스트 실행
#### 기능테스트
```python
from selenium import webdriver

browser = webdriver.Firefox()
browser.get('http://localhost:8000')

assert 'Django' in browser.title
```

#### unittest 모듈을 이용한 기능 테스트 확장
```python
from selenium import webdriver
import unittest

class NavigationTest(unittest.TestCase):
  
  def setUp(self):
    self.browser = webdriver.Firefox()

  def tearDown(self):
    self.browser.quit()

  def test_can_start_a_list_and_retrieve_it_later(self):
    # 웹 사이트 방문
    self.browser.get('http://localhost:8000')

    # 웹 페이지 타이틀 확인
    self.assertIn('To-Do', self.browser.title)

  if __name__ == '__main__':
    unittest.main(warnings='ignore')
```
#### 기능테스트 명령어 실행
```shell
$ python functional_test.py
```

