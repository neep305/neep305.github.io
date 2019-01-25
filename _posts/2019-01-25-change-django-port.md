---
layout: post
title: Change Django port
subtitle: Django 포트 변경
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,django,port]
---

### Changing port
If you want to change the server’s port, pass it as a command-line argument. For instance, this command starts the server on port 8080:
```bash
$ python manage.py runserver 8080
```

If you want to change the server’s IP, pass it along with the port. For example, to listen on all available public IPs (which is useful if you are running Vagrant or want to show off your work on other computers on the network), use:
```bash
$ python manage.py runserver 0:8000
```

0 is a shortcut for 0.0.0.0. Full docs for the development server can be found in the runserver reference.

