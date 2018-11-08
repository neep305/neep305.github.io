---
layout: post
title: Making a new directory
subtitle: 디렉토리 생성
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,mkdir]
---

### 디렉토리 생성

os.mkdir(path, mode=0o777, *, dir_fd=None)

Create a directory named path with numeric mode mode.

If the directory already exists, FileExistsError is raised.

On some systems, mode is ignored. Where it is used, the current umask value is first masked out. If bits other than the last 9 (i.e. the last 3 digits of the octal representation of the mode) are set, their meaning is platform-dependent. On some platforms, they are ignored and you should call chmod() explicitly to set them.

This function can also support paths relative to directory descriptors.

It is also possible to create temporary directories; see the tempfile module’s tempfile.mkdtemp() function.

New in version 3.3: The dir_fd argument.

Changed in version 3.6: Accepts a path-like object.
