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

- node 초기화 및 package.json 파일 생성 방법

  - ```command
    npm init

    D:\GitHub\web\web\bootcamp5_study\node>npm init
    package name: (node) node_study
    version: (1.0.0)
    description: desc.
    entry point: (01_helloworld.js)
    test command:
    git repository:
    keywords:
    author:
    license: (ISC)
    About to write to D:\GitHub\web\web\bootcamp5_study\node\package.json:

    {
      "name": "node_study",
      "version": "1.0.0",
      "description": "desc.",
      "main": "01_helloworld.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC"
    }

    Is this OK? (yes) yes
    ```

- Express 설치 방법

- ```command
  npm install express

  D:\GitHub\web\web\bootcamp5_study\node>npm install express

  added 57 packages, and audited 58 packages in 4s
  7 packages are looking for funding
    run `npm fund` for details
  found 0 vulnerabilities
  ```
  
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

- Node.js를 위한 빠르고 개방적인 간결한 웹 프레임워크
- BacnEnd 서버(API)를 구성하기 위한 오픈소스 기반의 프레임워크

> **IMPORTANT**
>> Express는 JavaScript로 작성되고 Node.js 런타임 환경에서 구동되는 인기 있는 웹 프레임워크
>>
>> - [Express NPM](https://www.npmjs.com/package/express)
>> - [Express 공식 싸이트](https://expressjs.com/)
>> - [MDN Express 공식 싸이트](https://developer.mozilla.org/ko/docs/Learn/Server-side/Express_Nodejs)
>> - 라우터로 인터프리터 방식으로 해석함(위에서 아래로)
>> - post 방식은 body > raw > json 형식으로 전송 { "param": {"id":3, "name": "walter", "email": "mail@mail.com" } }
>> - client -> server : body에 데이터보낼때 아래 옵션 필요
>>
>>> - `app.use(express.json({ limit: "50mb", }));`

```command
<!-- https://www.npmjs.com/package/express -->
>> npm i express
```

```javascript
// express
const express = require("express");
const app = express();
const port = 3000;

// 선언하지 않으면 오류 발생
app.use(
  express.json({
    limit: "50mb", // 최대 50메가
  })
);

app.listen(port, () => {
  console.log("서버가 포트 3000번으로 시작되었습니다.");
});

// 라우터 (주소+http method)
app.get("/", (req, res) => {
  res.send("Hello World");
});

// http://localhost:3000/customers get
app.get("/customers", (req, res) => {
  // db에 있는 고객 정보를 조회하고 클라이언트로 응답
  const customers = [
    { name: "John Doe", email: "john@gmail.com" },
    { name: "Jane Doe", email: "jane@gmail.com" },
  ];
  res.send(customers);
});

app.get("/customer/:id", (req, res) => {
  const id = parseInt(req.params.id);
  console.log("id", id);
  // db에 있는 고객 정보를 조회하고 클라이언트로 응답
  const customers = [
    { id: 1, name: "John Doe", email: "john@gmail.com" },
    { id: 2, name: "Jane Doe", email: "jane@gmail.com" },
  ];

  const customer = customers.filter((c) => c.id === id);
  if (customer.length > 0) res.status(200).send(customer[0]);
  else {
    res.status(401).send({ msg: "존재 하지 않는 ID 입니다." });
  }
});

app.post("/customer", (req, res) => {
  console.log(req.body.param);

  // 데이터베이스에 저장 코드

  res.send("Ok");
});
```

<img src="./../../assets/images/posts/bootcamp005/node_express_1.png" width="100%" align="center"/>
<br/><br/>
<img src="./../../assets/images/posts/bootcamp005/node_express_2.png" width="100%" align="center"/>

# 6. My SQL 연동

- MySQL은 세계에서 가장 많이 쓰이는 오픈 소스의 관계형 데이터베이스 관리 시스템이다

> **IMPORTANT**
>> Mac OS 설치 / [MySql 공식 싸이트](https://www.mysql.com/)
>>
>> - 무료 오픈소스 RDBMS이며, 다음의 중요한 명령어 참고
>> - brew list // 설치된 목록 조회
>> - brew services start mysql // mysql 서비스 시작
>> - brew services stop mysql / mysql 서비스 종료
>> - mysql_secure_installation // 초기 설정
>>
>>> - 간단한 비밀번호
>>> - anonymous user 제거
>>> - remotely disallow 
>>> - test database 제거
>>> - 변경된 권한 테이블에 적용
>>
>> - mysql -h localhost -u root -p // -h 접속주소, -u 접속 사용자
>> - mysql> status // utf8mb4 확인
>> - mysql> exit // 종료
>> - Workbench 설치
>>
>>> - <https://dev.mysql.com/downloads/workbench/>
>>> - mysql와 연동되어 명령어들을 수행할 수 있는 IDE

> **IMPORTANT**
>> Window OS 설치 / [MySql 공식 싸이트](https://www.mysql.com/)
>>
>> - 공식 다운로드 사이트 <https://www.mysql.com/downloads/>
>> - ‘Developer Default’ 선택으로 계속해서 설치
>> - 설치 완료 후 MySQL Workbench가 자동으로 실행 
>> - MySQL Command Line Client로 질의어 가능
>> - services를 통하여 MySql 서비스를 시작, 중단, 자동, 수동 설정 가

- 반드시 스키마 권한 설정이 필요하다
  - users and privileges > add account
  - login tab > standard authendication type으로 나머지 정보 입력
  - schema privileges tab
    - add entry > selected schema 선택 > 추가할 스키마 선택
    - select all 선택하여 모든 권한 부여
  
```command
<!-- https://www.npmjs.com/package/mysql -->
>> npm i mysql
```

```javascript
// mysql > index.js
// 가장 기본적인 연결 및 쿼리 샘플
var mysql = require("mysql");
var connection = mysql.createConnection({
  host: "127.0.0.1",
  port: 3306,
  user: "dev",
  password: "1234",
  database: "dev",
});

connection.connect();

connection.query(
  "SELECT * FROM dev.customers;",
  function (error, results, fields) {
    if (error) throw error;
    console.log(results);
  }
);

connection.end();
```

```javascript
// query script 모음
module.exports = {
  productList: `select * from customers`,
  categoryList: `select * from product_category`,
  categoryDetail: `select * from product_category where product_category_id = ?`,
  categoryInsert: `insert into product_category set ?`,
  // insert into product_category set category_name='', category_description='', use_yn=''
  categoryUpdate: `update product_category set ? where product_category_id = ?`,
  categoryDelete: `delete from product_category where product_category_id = ?`,
};
```

- 추천하는 방법으로는 connection pool을 만들고 만들 pool을 활용한다.
  
```javascript
// mysql 쿼리 실행을 위한 helper 함수
const mysql = require("mysql");
const sql = require("./sql");

const pool = mysql.createPool({
  host: "127.0.0.1",
  port: 3306,
  user: "dev",
  password: "1234",
  database: "dev",
  connectionLimit: 10,
});

const query = async (alias, values) => {
  return new Promise((resolve, reject) => {
    pool.query(sql[alias], values, (error, results) => {
      if (error) {
        console.log(error);
        reject(error);
      } else {
        resolve(results);
      }
    });
  });
};
```

```javascript
// 실제 사용 샘플
const express = require("express");
const app = express();
const port = 3000;
require("dotenv").config({ path: "mysql/.env" });
const mysql = require("./mysql");

app.use(
  express.json({
    limit: "50mb",
  })
);

app.listen(port, () => {
  console.log("서버가 포트 3000번으로 시작 했습니다.");
});

// (get) http://localhost:3000/api/products
app.get("/api/products", async (req, res) => {
  const productList = await mysql.query("productList");
  res.status(200).send(productList);
});

// (get) http://localhost:3000/api/categories
app.get("/api/categories", async (req, res) => {
  const categoryList = await mysql.query("categoryList");
  res.status(200).send(categoryList);
});

// (get) http://localhost:3000/api/category/4
app.get("/api/category/:product_category_id", async (req, res) => {
  const product_category_id = req.params.product_category_id;
  const categoryList = await mysql.query("categoryDetail", product_category_id);
  res.status(200).send(categoryList);
});

// (post) http://localhost:3000/api/category
app.post("/api/category", async (req, res) => {
  const result = await mysql.query("categoryInsert", req.body.param);
  res.status(200).send(result);
});

// (put) http://localhost:3000/api/category/8
app.put("/api/category/:product_category_id", async (req, res) => {
  const product_category_id = req.params.product_category_id;
  const result = await mysql.query("categoryUpdate", [
    req.body.param,
    product_category_id,
  ]);
  res.status(200).send(result);
});

// (delete) http://localhost:3000/api/category/:product_category_id
app.delete("/api/category/:product_category_id", async (req, res) => {
  const product_category_id = req.params.product_category_id;
  const result = await mysql.query("categoryDelete", product_category_id);
  res.status(200).send(result);
});
```

> **IMPORTANT**
>> `.env`
>>
>> - 환경변수를 만들어서 사용할 수 있도록 도와주며, 숨기고 싶은 정보를 위함
>> - `.gitignore` 파일에 `.env` 등을 명시하여 repogitory에 등록되지 않는다.
>> - npm을 통한 설치 `npm install dotenv`
>> - 개발시는 .env.test, 라이브시는 .env.prod 로 구분하여 사용, package.json > script 영역에 다음과 같이 구분하여 사용
>>
>>> - `npm install cross-env` 설치
>>> - "test": "cross-env NODE_ENV=test node 13_app_mysql.js"
>>> - "prod": "cross-env NODE_ENV=prod node 13_app_mysql.js"
>>> - app.get("env"); //NODE_ENV=test의 값인 'test or prod'를 가지고 온다.
>>> - require("dotenv").config({ path: `mysql/.env.${app.get("env")}` }); 와 같이 원하는 env 파일을 읽을 수 있다.

```javascript
// .env 파일
MYSQL_HOST = 127.0.0.1
MYSQL_PORT = 3306
MYSQL_USERNAME = dev
MYSQL_PASSWORD = 1234
MYSQL_DB = dev
MYSQL_LIMIT = 10
```

```javascript
// mysql 쿼리 실행을 위한 helper 함수의 pool 정의 부분이 env 파일 참조로 변경
const pool = mysql.createPool({
  host: process.env.MYSQL_HOST,
  port: process.env.MYSQL_PORT,
  user: process.env.MYSQL_USERNAME,
  password: process.env.MYSQL_PASSWORD,
  database: process.env.MYSQL_DB,
  connectionLimit: process.env.MYSQL_LIMIT,
});
```

```javascript
// 실제 사용 샘플에 다름의 env 파일 내용 추가하는 코드 추가
const envValue = app.get("env"); //NODE_ENV=test의 값인 'test or prod'를 가지고 온다.
require("dotenv").config({ path: `mysql/.env.${app.get("env")}` });
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

- MySql 설치 명령어 모음

> **IMPORTANT**
>> [MySql 공식 싸이트](https://www.mysql.com/)
>>
>> - 무료 오픈소스 RDBMS이며, 다음의 중요한 명령어 참고
>> - brew list // 설치된 목록 조회
>> - brew services start mysql // mysql 서비스 시작
>> - brew services stop mysql / mysql 서비스 종료
>> - mysql_secure_installation // 초기 설정
>>
>>> - 간단한 비밀번호
>>> - anonymous user 제거
>>> - remotely disallow 
>>> - test database 제거
>>> - 변경된 권한 테이블에 적용
>>
>> - mysql -h localhost -u root -p // -h 접속주소, -u 접속 사용자
>> - mysql> status // utf8mb4 확인
>> - mysql> exit // 종료
>> - Workbench 설치
>>
>>> - <https://dev.mysql.com/downloads/workbench/>
>>> - mysql와 연동되어 명령어들을 수행할 수 있는 IDE

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)