---
title:  "Nodejs"
excerpt: "개발자의품격"
comments: true
header:

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, nodejs]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-12-18
last_modified_at: 2022-12-18
---

- [1. Node.js](#1-nodejs)
- [2. Node.js 란?](#2-nodejs-란)
- [3. 자바스크립트 실행 및 모듈](#3-자바스크립트-실행-및-모듈)
- [참고](#참고)

# 1. Node.js

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Node.js_logo.svg/2560px-Node.js_logo.svg.png" width="100%" align="center"/>

- [Node.js 공식 사이트](https://nodejs.org/ko/)

# 2. Node.js 란?

- [Node.js 위키백과](https://ko.wikipedia.org/wiki/Node.js)
- `V8으로 빌드된 이벤트 기반 자바스크립트 런타임이다. 웹 서버와 같이 확장성 있는 네트워크 프로그램 제작을 위해 고안되었다.`

> **IMPORTANT**
>> 프로그램언어가 아니라 자바스크립트를 실행하는 환경
>>
>> - “node.js는 chrome v8 자바스크립크 엔진으로 빌드된 자바스크립트 런타임입니다”
>> - node.js 때문에 javascript 밖으로 나왓다
>> - 자바스크립트는 블로킹(blocking) 방식의 언어이라 node.js도 블로킹(blocking) IO 방식이다. 하지만 논블러킹(non blocking)으로 비동기 방식도 지원한다. 
>> - node.js의 특징은 싱글 스레드이고 이다. 하지만 이러한 약점을 극복하기위해 논블로킹 사용
>> - 또다른 특징은 이벤트 루프(libuv)를 통하여 논블러킹을 지원하고 처리할 함수 목록을 스케줄링 한다
  
# 3. 자바스크립트 실행 및 모듈

- Javascript 코드를 빌드하고 실행

> **IMPORTANT**
>> `node` 패키지 명령어를 통하여 cli 관경에서 Javascript 코드 실행
>>
>> - `node 01_helloworld`와 같이 node 패키지를 사용하여 cli 환경에서 실행 가능
>> - `module.export = {}`의 형식으로 export하기 위한 함수 정의
>> - export 된 함수를 `const { xx, yy } = require()` 함수를 사용하여 import하여 사용

```javascript
// 02_calculator.js
function add(n1, n2) {
  return n1 + n2;
}

function minus(n1, n2) {
  return n1 - n2;
}

function mul(n1, n2) {
  return n1 * n2;
}

function divide(n1, n2) {
  return n1 / n2;
}

const defaultNum = 1;

module.exports = {
  add,
  minus,
  mul,
  divide,
  defaultNum,
};

// 03_module.js
const { add, minus, defaultNum } = require("./02_calculator");

console.log(add(7, 2));
console.log(minus(7, 2));
console.log(defaultNum);
```

# 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)