---
layout: post
title: Remote 서버에 파일 복사하기
subtitle: scp command 사용법
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [scp,ssh,ssh-keygen,remote-copy]
---

### 1. Key 생성
> ssh key 생성: 주의할 점!!! 비밀번호를 입력하지 않는다. 모두 엔터로 처리

```shell
$ ssh-keygen -t rsa -b 4096 -C “neep305@gmail.com"
```

### 2. 로컬PC에 생성된 Public Key 복사
> 로컬에 있는 퍼블릭키를 복사 

```shell
$ cat id_rsa.pub # copy and paste
```

### 3. 리모트서버 authorized_keys에 로컬PC에서 복사한 Public Key 추가
> 리모트서버(파일을 전송하고 싶은 서버)에 접속하여 .ssh/authroized_keys를 열고, 로컬(소스서버)의 public key를 복사한다.

```shell
$  vi .ssh/authroized_keys # copy and save
```