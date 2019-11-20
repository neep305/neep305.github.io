---
layout: post
title: MongoDB Config 변수 작성하기
subtitle: config.js에 정리하기
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [mongodb,mongoose,nodejs,configjs]
---

### 설정 관련 고정값들을 Config.js 파일에 정리한다.
```javascript
var config = {
    VERSION: 1,
    BUILD: 1,
    URL: 'http://127.0.0.1',
    API_PATH : '/api',
    PORT : process.env.PORT || 8080,
    DB : {
    //MongoDB configuration
    HOST : 'localhost',
    PORT : '27017',
    DATABASE : 'db'
},
/*
* Get DB Connection String for connecting to MongoDB database
*/
getDBString : function(){
    return 'mongodb://'+ this.DB.HOST +':'+ this.DB.PORT +'/'+ this.DB.DATABASE;
},
/*
* Get the http URL
GoalKicker.com – Node.js Notes for Professionals 184
*/
getHTTPUrl : function(){
    return 'http://' + this.URL + ":" + this.PORT;
}

module.exports = config;
```