---
layout: post
title: Pinterest app 개발하기
subtitle: using pintrest api and development
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [pintrest,oauth,nodejs]
---

# Getting started

## 앱 만들기
> Pintrest 개발사이트 내용을 기준으로 정리하였음

 ```python
1. https://developers.pinterest.com/apps/ 접속
2. Create app 클릭: App 이름 및 Description 작성 
 ```

## Authentication

```shell
https://api.pinterest.com/oauth/?response_type=code&redirect_uri=https://mywebsite.com/connect/pinterest/&client_id=12345&scope=read_public,write_public&state=768uyFys
```