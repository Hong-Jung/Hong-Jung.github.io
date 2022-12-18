---
title:  "Node.js"
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
- [4. 내장 모듈](#4-내장-모듈)
- [5. Express](#5-express)
- [6. My SQL 연동](#6-my-sql-연동)
- [7. Express 라우터](#7-express-라우터)
- [8. 정적 파일 처리](#8-정적-파일-처리)
- [9. 파일 업로드](#9-파일-업로드)
- [10. 엑셀 업로드 및 파싱](#10-엑셀-업로드-및-파싱)
- [11. HTTP 응답 로그 관리](#11-http-응답-로그-관리)
- [12. 개발자 로그 관리](#12-개발자-로그-관리)
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

# 4. 내장 모듈

- console, timer, process, path, url, crypto, fs

> **IMPORTANT**
>> [console](https://nodejs.org/docs/latest-v17.x/api/console.html)
>>
>> - 전역 객체임으로 별도의 import 없이 사용가능
>> - console.log, console.log(new Exception("error")) // 단순 로그
>> - console.error // 에러 로그
>> - console.table(arr) // 테이블 형태의 로그
>> - console.dir(obj, {depth:1, color:true}) // 객체 깊이별로 확인
>> - console.time("동일한 레이블") ~~ console.timeEnd("동일한 레이블") // 함수의 시간 소요 확인

```javascript
const fs = require("fs"); // filesystem
const { Console } = require("console");

const output = fs.createWriteStream("./stdout.log");
const errorOutput = fs.createWriteStream("./stderr.log");

const logger = new Console({ stdout: output, stderr: errorOutput });
const count = 5;
logger.log("count: %d", count);
logger.error("count: " + count);

console.log("Hello World");
const world = "world";
console.log(`hello ${world}`);

console.error("에러 메시지 출력");
console.error(new Error("에러 메시지 출력"));

const arr = [
  { name: "John Doe", email: "john@gmail.com" },
  { name: "Jane Doe", email: "jane@gmail.com" },
];

console.log(arr);
console.table(arr);

const obj = {
  students: {
    grade1: { class1: {}, class2: {} },
    grade2: { class1: {}, class2: {} },
    teachers: ["John Doe", "Jane Doe"],
  },
};

console.log(obj);

console.dir(obj, { depth: 1, color: true });

console.time("func 1");
for (let i = 0; i < 999999; i++) {
  // 특정 코드
}
console.timeEnd("func 1");
```

> **IMPORTANT**
>> [timer](https://nodejs.org/docs/latest-v17.x/api/timers.html)
>>
>> - 전역 객체임으로 별도의 import 없이 사용가능
>> - setTimeout() // 밀리세컨트 이 후 한번 실행
>> - setInterval(), clearInterval() // 밀리세컨트 이 후 반복해서 실행
>> - setImmediate() // 시간없이 callback 함수만 작성, 이 후 모든 코드 먼저 실행 후 실행 됨

```javascript
const timeout = setTimeout(() => {
  console.log("1초 후에 실행됩니다.");
}, 1000);

const interval = setInterval(() => {
  console.log("1초 마다 실행이 됩니다.");
}, 1000);

setTimeout(() => {
  clearInterval(interval);
}, 3000);

const immediate = setImmediate(() => {
  console.log(
    "setImmediate() 함수 호출 뒤에 오는 모든 코드를 먼저 실행하고 바로 다음에 실행이 됩니다."
  );
});

console.log("setImmediate 보다 먼저 실행 됩니다.");
```

> **IMPORTANT**
>> [process](https://nodejs.org/docs/latest-v17.x/api/process.html)
>>
>> - 전역 객체가 아님으로 require로 import 후 사용 가능
>> - 특정 이벤트 발생시 마다 이벤트 캐취를 위한 리스너 등록 후 사용 가능
>> - 
>> - 

```javascript
const process = require("process");

console.log(process.env);

process.on("beforeExit", (code) => {
  console.log("beforeExit 이벤트 리스너", code);
});

process.on("exit", (code) => {
  console.log("exit 이벤트 리스너", code);
});

console.log("1. 콘솔에 출력되는 첫 번째 메시지");
console.log("2. 콘솔에 출력되는 두 번째 메시지");
```

> **IMPORTANT**
>> [os](https://nodejs.org/docs/latest-v17.x/api/child_process.html)
>>
>> - 전역 객체가 아님으로 require로 import 후 사용 가능
>> - 운영체제의 정보 확인

```javascript
const os = require("os");

console.log(os.arch()); // CPU 아키텍쳐
console.log(os.cpus()); // CPU 코어 정보
console.log(os.hostname()); // 운영체제 호스트명
console.log(os.type()); // 운영체제 타입
console.log(os.tmpdir()); // 임시 파일 저장 경로
```

> **IMPORTANT**
>> [path](https://nodejs.org/docs/latest-v17.x/api/path.html)
>>
>> - 전역 객체가 아님으로 require로 import 후 사용 가능
>> - 경로에 대한 전반적인 정보

```javascript
const path = require("path");

console.log(__dirname); // 현재 실행되고 있는 파일의 디렉토리 경로
console.log(__filename); // 현재 실행되고 있는 파일의 경로

console.log(path.basename(__filename)); // 경로의 마지막 부분
console.log(path.basename(__filename, ".js")); // 경로의 마지막 부분에서 확장자를 제거한 이름

console.log(path.dirname(__filename)); // 파일의 디렉토리 경로
console.log(path.dirname("dir1/dir2/dir3/file.js"));

console.log(path.extname(__filename)); // 파일의 확장자

console.log(path.parse("/home/user/dir/file.txt"));
const path1 = path.parse("/home/user/dir/file.txt");
console.log(path1.name);
// {
//     root: '/',
//     dir: '/home/user/dir',
//     base: 'file.txt',
//     ext: '.txt',
//     name: 'file'
//   }

const path2 = path.format({
  root: "/",
  dir: "/home/user/dir",
  base: "file.txt",
  ext: ".txt",
  name: "file",
});

console.log(path2);
console.log(path.join("/home", "user", "dir", "file.txt"));
```

> **IMPORTANT**
>> [url](https://nodejs.org/docs/latest-v17.x/api/url.html)
>>
>> - 전역 객체임으로 바로 사용 가능
>> - URL 관련한 오브젝트

```javascript
const myURL = new URL(
  "https://user:pass@sub.example.com:8080/p/a/t/h?query=string#hash"
);

console.log(myURL);
console.log(myURL.username); // username
console.log(myURL.password); // 비번

const myURL2 = new URL("https://example.org?user=abc&query=xyz&sort=asc");

const user = myURL2.searchParams.get("user");
const query = myURL2.searchParams.get("query");
const sort = myURL2.searchParams.get("sort");

console.log(myURL2.searchParams.keys());
console.log(myURL2.searchParams.values());

myURL2.searchParams.append("user2", "def"); // 새로운 키로 추가 가능
myURL2.searchParams.append("user", "def"); // 기존에 있는 키로 값을 추가하면, 동일한 키가 있으면 그대로 유지하고 하나 더 추가
myURL2.searchParams.set("user", "def"); // 동일한 키가 있으면, 기존 키를 삭제하고 새로 추가해야
console.log(myURL2);

console.log(myURL2.searchParams.getAll("user"));
myURL2.searchParams.delete("user"); // 해당 키를 삭제

console.log(myURL2.searchParams.toString());
```

> **IMPORTANT**
>> [crypto](https://nodejs.org/docs/latest-v17.x/api/crypto.html)
>>
>> - 전역 객체가 아님으로 require로 import 후 사용 가능
>> - URL 관련한 오브젝트

```javascript
const crypto = require("crypto");

const pw = "pw1234";

// createHash - 암호화 알고리즘
// digest - 인코딩 방식
const cryptoPW = crypto.createHash("sha512").update(pw).digest("base64");
console.log(cryptoPW); // 9iSeOd1vv2qinR2UM5Aog5LmqBncF/oFeTTsPUjqwGoG3lG232280LqAScE7FR7HHe4K0gyedCN7iZDZl+NZaA==

const cryptoPW2 = crypto.createHash("sha512").update(pw).digest("hex");
console.log(cryptoPW2); // f6249e39dd6fbf6aa29d1d943390288392e6a819dc17fa057934ec3d48eac06a06de51b6df6dbcd0ba8049c13b151ec71dee0ad20c9e74237b8990d997e35968

// 레인보우 테이블 - 원본값과 다양한 암호화 알고리즘 결과를 가지고 있는 테이블
// pw1, sha512-base64, sha512-hex
// pw2
// 해커가 레인보우 테이블을 가지고 있더라도, 원래 평문을 알기 굉장히 어렵게 처리해야함.
// salting 암호화

const createSalt = () => {
  return new Promise((resolve, reject) => {
    crypto.randomBytes(64, (err, buf) => {
      if (err) reject(err);

      resolve(buf.toString("base64"));
    });
  });
};

const createCryptoPassword = async (plainPassword) => {
  const salt = await createSalt();
  //
  console.log(salt);

  return new Promise((resolve, reject) => {
    // 암호화할 평문, salt, 반복횟수, 출력할 바이트수, 해시 알고리즘, 콜백 함수
    crypto.pbkdf2(plainPassword, salt, 100000, 64, "sha512", (err, key) => {
      if (err) reject(err);

      resolve({ password: key.toString("base64"), salt: salt });
    });
  });
};

const test = async () => {
  const r = await createCryptoPassword("pw1234");
  console.log(r);
};

test();

const getCryptoPassword = (plainPassword, salt) => {
  return new Promise((resolve, reject) => {
    // 암호화할 평문, salt, 반복횟수, 출력할 바이트수, 해시 알고리즘, 콜백 함수
    crypto.pbkdf2(plainPassword, salt, 100000, 64, "sha512", (err, key) => {
      if (err) reject(err);

      resolve({ password: key.toString("base64"), salt: salt });
    });
  });
};

// 사용자가 로그인 하는 시점에 비번을 입력하면,
// 사용자 아이디, 비밀번호
// 데이터베이스에서 사용자 아이디를 조건으로 저장되어 있는 암호화된 비밀번호와 salt
// getCryptoPassword함수에 로그인 시 입력한 비밀번호 평문과 데이터베이스에서 조회한 salt 값을 전달
// 데이터베이스에 저장된 암호화된 비밀번호와 gwetCrytoPassword 함수로 전달받은 암호화된 password 값이 같은지 확인
// 같으면 로그인 처리
```

> **IMPORTANT**
>> [fs-filesystem](https://nodejs.org/docs/latest-v17.x/api/fs.html)
>>
>> - 전역 객체가 아님으로 require로 import 후 사용 가능
>> - 파일 시스템 관련 객체, 동기/비동기 함수가 함께 존재

```javascript
const fs = require("fs");
// fs - filesystem

fs.readFile("./sample/text.txt", "utf8", (err, data) => {
  if (err) {
    throw err;
  }

  console.log(data);
});

console.log("1");

const data = fs.readFileSync("./sample/text.txt", "utf8");
console.log(data);

const txt = "파일 쓰기 테스트";
fs.writeFile("./sample/text_w.txt", txt, "utf8", (err) => {
  if (err) {
    throw err;
  }

  const data2 = fs.readFileSync("./sample/text_w.txt", "utf8");
  console.log(data2);
});

const txt2 = "파일 쓰기 테스트 동기 방식";

fs.writeFileSync("./sample/text_w2.txt", txt2, "utf8");
const data2 = fs.readFileSync("./sample/text_w2.txt", "utf8");
console.log(data2);
```

# 5. Express

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 6. My SQL 연동

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 7. Express 라우터

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 8. 정적 파일 처리

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 9. 파일 업로드

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 10. 엑셀 업로드 및 파싱

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 11. HTTP 응답 로그 관리

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 12. 개발자 로그 관리

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```

# 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)