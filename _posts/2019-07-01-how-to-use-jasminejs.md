---
layout: post
title: Jasmine 사용한 TDD 개발
subtitle: Nodejs TDD
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [nodejs,javascript,jasmine,tdd,frontend]
---

다른 개발자는 다 아는데 혼자만 모르는 Jasmine 사용한 TDD 정리해보기

### Jasmine - Home
[Github 메인페이지 이동하기](https://jasmine.github.io/index.html)

### Jasmine 설치/세팅
| 패키지 설치하기
```shell
$ npm install --save-dev jasmine
```

| 프로젝트 초기화
```shell
$ node node_modules/jasmine/bin/jasmine init
```
 실행 시 root 경로 밑에 spec 폴더가 자동 생성된다.

| package.json script 영역에 "test":"jasmine" 추가
```javascript
script: {
    "test":"jasmine",
    "start":"node server.js"
}
```

| test script 실행하기
```shell
$ npm test
```

### Jasmine 테스트 코드 작성하기
| e.g. server_spec.js란 파일을 spec 폴더 밑에 생성 후 테스트 코드 작성
```javascript
describe('calc', () => {
    it('Multiply 2 and 2', () => {
        expect(2*2).toBe(4)
    })
})

describe('get messages', () => {
    it('should return 200 ok', (done) => {
        request.get('http://localhost:3000/messages', (err, res) => {
            expect(res.statusCode).toEqual(200)
            done()
        })
    })
    it('should return a list, not empty', (done) => {
        request.get('http://localhost:3000/messages', (err, res) => {
            expect(res.body.length).toBeGreaterThan(40)
            done()
        })
    })
})
```