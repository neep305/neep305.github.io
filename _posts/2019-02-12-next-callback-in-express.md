---
layout: post
title: Express에서 next callback 사용하기
subtitle: next 사용여부에 따른 미들웨어 동작 이해
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [nodejs,callback,middleware,expressjs]
---

### app.use()를 선언하여 middleware를 로드한다.
> 예를 들면 아래와 같이 myLogger를 미들웨어에 등록하면 routerhandler를 통해 '/'(루트경로)가 호출되기 전에 항상 myLogger가 호출되게 된다. 여기에 next()를 선언하면 다음 middleware로 request가 전달하게 된다.
반대로 app.use(myLogger)가 routerhandler 뒤에 있는 경우에는 다음 middleware로 request가 전달되지 않는다.

~~~javascript
var express = require('express')
var app = express()

var myLogger = function (req, res, next) {
  console.log('LOGGED')
  next()
}

app.use(myLogger)

app.get('/', function (req, res) {
  res.send('Hello World!')
})

app.listen(3000)
~~~