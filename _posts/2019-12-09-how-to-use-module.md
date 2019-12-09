---
layout: post
title: node.js에서 module 사용하기
subtitle: module.exports
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [node.js,module,exports]
---

# 모듈

> users.js
```javascript
var CLIENT_KEY = process.env.CLIENT_KEY

exports.getKey = function() {
    return CLIENT_KEY;
}

exports.user = {
    id: 'tester',
    name: 'Jason'
}
```

> index.js
```javascript
var users = require('./users');

console.log(users.getKey());
consoloe.log(users.user);
```