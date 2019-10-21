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
from selenium.webdriver.common.keys import Keys
import unittest

class NavigationTest(unittest.TestCase):
  
  def setUp(self):
    self.browser = webdriver.Firefox()
    # 브라우저 실행 후 3초를 기다리도록 명령. 렌더링 속도 혹은 사이트에 따라 3초를 맞춰 어떤 동작을 실행할 경우 정확히 의도한 동작을 실행하기 어려울 수 있음.
    self.browser.implicitly_wait(3)

  def tearDown(self):
    self.browser.quit()

  def test_can_start_a_list_and_retrieve_it_later(self):
    # 웹 사이트 방문
    self.browser.get('http://localhost:8000')

    # 웹 페이지 타이틀 확인
    self.assertIn('To-Do', self.browser.title)
    header_text = self.browser.find_element_by_tag_name('h1').text
    self.assertIn('To-Do', header_text)

    inputbox = self.browser.find_element_by_id('id_new_item')
    self.assertEqual(inputbox.get_attribute('placeholder'), 'add new item')

    inputbox.send_keys('Buy shoes')
    inputbox.send_keys(Keys.ENTER)

    table = self.browser.find_element_by_id('id_list_table')
    rows = table.find_elements_by_tag_name('tr')
    self.assertTrue(any(row.text == '1: Buy shoes' for row in rows),)

    self.fail('Finish the test!!')

  if __name__ == '__main__':
    unittest.main(warnings='ignore')
```
#### 기능테스트 명령어 실행
```shell
$ python functional_test.py
```