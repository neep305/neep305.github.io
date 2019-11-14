---
layout: post
title: Python logging module 사용하기
subtitle: Basic and custom logging
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,logging]
---

### Using the logging module

#### 기본 로깅 
> level 및 output 파일경로를 설정한다.

```python

import logging

def main():
  logging.basicConfig(level=logging.DEBUG, filename="output.log",filemode="w")

  logging.debug("debug-level message")
  logging.info("info-level message")
  logging.warning("warning-level message")
  logging.error("error-level message")
  logging.critical("critical-level message")

  logging.info("Here's a {} variable and an int".format("string", 10))

if __name__ == "__main__":
  main()
```

#### 커스텀 로깅

|함수|설명|
|-|-|
|%(asctime)s| Human readable date format when the log record was created|
|%(filename)s| File namw where the log message originated|
|%(funcName)s| Function name where the log message originated|
|%(levelname)s| String representation of the message level(DEBUG, INFO, etc.)
|%(levelno)d| Numeric representation of the message level|
|%(lineno)d| Source line number where the logging call was issued (if available)|
|%(message)s| The logged message string itself|
|%(module)s| Module name portion of the filename where the message was logged|


#### 커스텀 로깅 예제
```python

import logging

extData = {
  'user': 'jason@example.com'
}

def anotherFunction():
  logging.debug("This is a debug-level message",extra=extData)


def main():
  fmtstr = "User:%(user)s %(asctime)s: %(levelname)s: %(funcName)s Line:%(lineno)d %(message)s"

  datestr = "%m/%d/%Y %I:%M:%S %p"
  logging.basicConfig(filename="output.log", level=logging.DEBUG,
  filename="w",
  format=fmtstr,
  datefmt=datestr)

  logging.info("info level log message", extra=extData)
  anotherFunction()


if __name__ == "__main__":
  main()
```