---
layout: post
title: Async/Await
subtitle: Asynchronous code in a procedural manner 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [nodejs,javascript,async_await,callback,promise]
---

# Comparison between 'Promise' and 'Async/Await'

## Promise 

```javascript
function myAsyncFunction(){
  return myPromiseFunction().then(result => doSomething(result)).catch(handleError);
}
```

## Async
async function myAsyncFunction(){
  let result;
    
  try {
    result = await myPromiseFunction();
  } catch (err) {
    handleError(error);
  }

  return doSomething(result);
}
