---
layout: post
title: JavaScript에서 Callback을 어떻게 사용하는가?
subtitle: Javascript callback functions explained 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,flask,swagger]
---

# How to use callbacks in JavaScript

## Functions are Objects
- JavaScript에서 function은 1급 오브젝트(first-class object)이다. 따라서 다른 오브젝트들처럼 function도 같은 방식으로 사용이 가능하다.
  - 변수를 할당하거나
  - 다른 function에 argument로 사용할 수 있다.

## Callback Functions

> case 1. declare an explicit function name, logQuote
```javascript
function createQuote(quote, callback){ 
  var myQuote = "Like I always say, " + quote;
  callback(myQuote); // 2
}

function logQuote(quote){
  console.log(quote);
}

createQuote("eat your vegetables!", logQuote); // 1
```

> case 2. using an anonymous function as a parameter

- Same as case 1

```javascript
function createQuote(quote, function(quote) {
  console.log(quote);
});
```

> case 3. callback function name doesn't need to be named "callback()"

```javascript
// We use callback function name as 'callback' of 2nd parameter 
function createQuote(quote, callback) { 
  var myQuote = "Like I always say, " + quote;
  callback(myQuote);
}

// We use callback function name as 'functionToCall' of 2nd parameter
function createQuote(quote, functionToCall) { 
  var myQuote = "Like I always say, " + quote;
  functionToCall(myQuote);
}
```

## Why use callbacks?

> Most of the time we are creating programs and applications that operate in a synchronous manner. In other words, some of our operations are started only after the preceding ones have completed. Often when we request data from other sources, such as an external API, we don’t always know when our data will be served back. In these instances we want to wait for the response, but we don’t always want our entire application grinding to a halt while our data is being fetched. These situations are where callback functions come in handy.
<br>우리가 만드는 대부분의 프로그램과 어플리케이션은 **동기 방식(synchronous manner)** 으로 동작합니다. 다른 방식으로 말하자면, 동작하는 것 중에 어떤 것들은 하나가 끝난 후에 진행이 된다는 뜻입니다.
<br>그러나 종종 우리가 외부 API와 같은 다른 소스에 데이터를 요청할 때, 우리가 데이터를 언제 받을 수 있는지 타이밍을 정확히 알 수 없습니다. 예를 들어 API 요청 후 응답이 오는 것을 기다려야 하지만, 이로 인해 데이터를 가져올 때까지(fetch) **어플리케이션 전체가 멈춘 상태(grind to a halt)** 로 있으면 안됩니다. 
<br>따라서 이러한 경우에 Callback function을 쓰면 유용합니다.

### 예제1

```javascript
// Result in console after 5 second delay:
// Response from the server: The glass is half full!
function serverRequest(query, callback){
  setTimeout(function(){
    var response = query + "full!";
    callback(response);
  },5000);
}

function getResults(results){
  console.log("Response from the server: " + results);
}

serverRequest("The glass is half ", getResults);
```

### 예제2
```javascript
function getResult(param, callback) {
  callback({result:"ok", data:{msg: "login success", token:"1234"}})
}

getResult(null, function(param){
  console.log(param);
});

// 출력 결과값: {result:"ok", data:{msg: "login success", token:"1234"}}
```