---
layout: post
title: pip SSL Error on Windows
subtitle: pip 설정 및 명령어 옵션 정리 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python, pip, ssl, config]
---

# Getting started
- 윈도우즈에서 pip 명령어 실행시 예상치 못한 SSL, Timeout 발생하는 경우를 경험해서 정리해봤습니다.
### SSL Verification & Timout 세팅
- Stack overflow [링크](https://stackoverflow.com/questions/49943410/pip-ssl-error-on-windows)

> 방법1. pip.ini 사용: pip.ini는 임시로 만들어야 함
```
# pip.ini가 설치된 경로 리스트를 확인한다.
pip config -v list

# virtualenv에 별도로 pip.ini를 만들려면 venv 폴더 바로 밑에 pip.ini를 생성한다.
[global]                                                                                                                        
trusted-host = pypi.python.org pypi.org files.pythonhosted.org
timeout=1000 # 타임아웃 발생할 경우가 있어 타임아웃시간도 설정
```

> 방법2. cli 명령어 옵션
```
# trusted-host
pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org <package>

# Default Timeout
pip install <pkg> --default-timeout=10000
```

### 참고
- pip guide: https://pip.pypa.io/en/stable/user_guide/
