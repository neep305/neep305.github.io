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
console.log(users.user);
```

## module.export 사용하여 객체 그대로 할당하기

> test.js

```javascript
var users = {
    getUser: function(){
        return {id:'tester',name:'Jason'}
    },
    group: {id: 'test-group', name: 'DevOps'}
}

module.exports = users;
```