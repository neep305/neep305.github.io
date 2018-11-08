---
layout: post
title: Create and run a requirements.txt for pip install
subtitle: Example of requirements.txt
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,install,package-management]
---

### Create a requirements.txt
> Add name of library like below. 
```shell
Django==1.9.6
requests==2.18.4
selenium
google-cloud-bigquery
httplib2
```

> If you don't input specific version, it will be installed the latest version automatically

### Record package list of current environment
```shell
$ pip freeze > requirements.txt
```

### Run requirements.txt
```shell
$ pip install -r requirements.txt -v
```

### Helpful contents about this
[Essential package management using requirements.txt](https://docs.microsoft.com/ko-kr/visualstudio/python/managing-required-packages-with-requirements-txt?view=vs-2017)
