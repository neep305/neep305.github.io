---
layout: post
title: 새로운 ssh key 생성하고 ssh-agent에 추가하기
subtitle: Github에 public key 추가하기
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [github,ssh,ssh-keygen,ssh-agent]
---

### SSH 키 새로 생성하기
- 아래 명령어를 입력하고 메일주소에 Github 계정에서 쓰는 메일주소를 입력한다.

```shell
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

> Generating public/private rsa key pair.
> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
> Enter passphrase (empty for no passphrase): [Type a passphrase]> Enter same passphrase again: [Type passphrase again]
```

### Adding your SSH key to the ssh-agent
1. ssh-agent를 백그라운드에서 실행한다.
```shell
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```

2. 맥OS Sierra 10.12.2 또는 이후 버전은 ~/.ssh/config 파일을 수정해야 한다.
```shell
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

3. private key를 ssh-agent에 추가하고, passpharase를 키체인에 저장한다.
```shell
$ ssh-add -K ~/.ssh/id_rsa
```

4. Github Setting > SSH and GPG keys에 접속하여 SSH key를 새로 추가한다.