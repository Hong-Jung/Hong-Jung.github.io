---
title:  "JavaScript"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, JavaScript]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-24
last_modified_at: 2022-10-24
---

<!-- <img src="../../assets/images/posts/bootcamp005/개발자의품격001.png" width="100%"/> -->

## 0. Index

- [0. Index](#0-index)
- [1. JavaScript 란?](#1-javascript-란)
  - [1.1 역사](#11-역사)
  - [1.2 표준재정](#12-표준재정)
  - [1.3 바닐라스크립트](#13-바닐라스크립트)
- [2. JavaScript 작성 위치](#2-javascript-작성-위치)
  - [2.1 작성 위치](#21-작성-위치)
  - [2.2 추천 위치](#22-추천-위치)
- [4. 변수 선언자(var, let, const)](#4-변수-선언자var-let-const)
  - [4.1 변수명명 규칙](#41-변수명명-규칙)
  - [4.2 변수 선언자(var, let, const)](#42-변수-선언자var-let-const)
- [5. 기본 데이터 타입](#5-기본-데이터-타입)
  - [5.1 Object 타입](#51-object-타입)
  - [5.2 Array 타입](#52-array-타입)
  - [5.3 64 비트 부동소수점](#53-64-비트-부동소수점)
- [6. 연산자(할당, 비교, 산술, 논리, 문자열, 조건삼항)](#6-연산자할당-비교-산술-논리-문자열-조건삼항)
- [7. 조건문](#7-조건문)
- [8. 반복문](#8-반복문)
- [9. 함수](#9-함수)
- [10. 주요 객체와 내장 함수](#10-주요-객체와-내장-함수)
  - [10.1 String](#101-string)
  - [10.2 Number](#102-number)
  - [10.3 Array](#103-array)
  - [10.4 Date](#104-date)
  - [10.5 Set](#105-set)
  - [10.6 Map](#106-map)
  - [10.7 Math](#107-math)
  - [10.8 JSON](#108-json)
  - [10.9 window](#109-window)
- [11. Reference](#11-reference)

## 1. JavaScript 란?

### 1.1 역사

- [JavaScript의 역사](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)
  - 1990년대 넷스케이프 회사의 Brendan Eich가 처음 Mocha이름으로 개발 후 LiveScript를 거처 JavaScirpt로 되었음
  - Microsoft도 인터넷 익스플로러 전용 JScript를 개발, 이때부터 표준화가 이슈화 됨

### 1.2 표준재정

- [ECMA Script(ES)](https://ko.wikipedia.org/wiki/ECMA%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)
  - 스크립트 표준 규격인 [ECMA-262](https://www.ecma-international.org/technical-committees/tc39/?tab=general) 채택됨
  - JavaScirpt는 언어이며, ECMA Script는 스크립트 표준
  - ECMA Script = ES

### 1.3 바닐라스크립트

- [Valilla JavaScript](http://vanilla-js.com/)
  - 순수 자바스크립트로 어떠한 라이브러리도 사용하지 않음
  - 슬로건
    - Vanilla JS is a fast, lightweight, cross-platform framework
for building incredible, powerful JavaScript applications.

## 2. JavaScript 작성 위치

### 2.1 작성 위치

- 헤더영역에 인라인으로 작성

  - ```html
    <head>
      <script>
        document.write("hello.!!");
      </script>
    </head>
    <body></body>
    ```

- 바디 어디든 작성

  - ```html
    <body>
      <script>
        document.write("hello.1");
      </script>
      <h1>머리말1</h1>
      <script>
        document.write("hello.2");
      </script>
    </body>
    ```

- 외부 파일 작성

  - ```javascript
    <!-- ./js/js_location.js -->
    document.write("별도의 js 파일에서 document.write 실행");
    ```

  - ```html
    <head>
      <script src="./js/js_location.js"></script>
    </head>
    ```

- 순차적으로 코드를 분석(인터프리터 방식) 및 로딩으로 바디 태그 아래에 두는 것이 퍼포먼스측면에서 가장 좋다.

  - `defer` 속성을 사용하여 `<head></head>`에 정의된 script도 `<body></body>` 태그 하단에서 로딩

  - ```html
    <head>
      <script src="./js/js_location.js" defer></script>
    </head>
    ```

### 2.2 추천 위치

- 하단의 외부참조부터 넣고, 해당 파일만의 스크립트 태그 작성

- ```html
  <body>
    <h1>본문 내용</h1>
    <script src="./js/js_location.js"></script>
    <script>
      <!-- 해당 html 파일에서만 사용되는 JavaSciprt 코드 정의 -->
    </script>
  </body>
  ```

## 3. Console 객체의 log 함수

- `console.log` 함수를 사용해 원하는 값을 콘솔에 출력 가능

- ```html
  <body>
    <script>
      <!-- window.console 객체의 log 함수의 문자열 파라메터를 사용하여 로그 출력 -->
      console.log('hello !');
    </script>
  </body>
  ```

## 4. 변수 선언자(var, let, const)

- 변수란?
  - 데이터를 넣기 위한 단위 그릇
- 자바나 C#과 같은 강력한 형식이 존재하는 언어는 어떤 데이터를 담을지에 따라서 그릇의 형태를 다르게 해야 한다.
- 자바스크립트의 경우는 어떠한 형식(문자, 숙자, 날짜, 소숫점등)이든 데이터를 담는 그릇이 동일하다.
- 편함에 있어서는 장점이 될 수 도 있지만, 사전에(개발시) 다양한 데이터 형식으로 인한 오류를 잡지 못하는 상황이 생김
- 타입스크립트 : 기존의 이러한 자바스크립트의 단점을 보완, 형식을 지정

- 데이터를 담기 위하여 변수를 선언
  - 변수라고 알려주기 위해서는 "변수 선언자"가 필요
  - ES6 이전에는 변수 선언자는 "var" 뿐임
  - ES6 이후에는 변수 선언자는 "var, let, const"와 같이 다양해짐

### 4.1 변수명명 규칙

- **변수 선언자(var, let, const)**를 이용하여 변수를 선언할때 이름을 지어주어야 한다. 이럴때 다음과 같이 많이 사용하는 명명규칙이 있다.
  - [카멜표기법(camelCase)](https://ko.wikipedia.org/wiki/%EC%B9%B4%EB%A9%9C_%ED%91%9C%EA%B8%B0%EB%B2%95)
    - ```javascript var userName = "walter";```
  - [스네이크 표기법(snake_case)](https://ko.wikipedia.org/wiki/%EC%8A%A4%EB%84%A4%EC%9D%B4%ED%81%AC_%ED%91%9C%EA%B8%B0%EB%B2%95)
    - ```javascript var user_name = "walter";```
  - 파스칼 표기법(PascalCase)
    - ```javascript var UserName = "walter";```
  - [헝가리언 표기법(데이터타입의 약어사용)](https://ko.wikipedia.org/wiki/%ED%97%9D%EA%B0%80%EB%A6%AC%EC%95%88_%ED%91%9C%EA%B8%B0%EB%B2%95)
    - ```javascript var strUserName = "walter";```
  - ES6에서도 카멜표기법을 따라서 사용하며, 일반적으로 가장 많이 사용

### 4.2 변수 선언자(var, let, const)

- var, let, const의 차이점
  - var
    - 선언한 변수명에 데이터를 다시 할당할 수 있음

      - ```javascript
        var x = 5;
        var y = 7;
        var z = x + y; // 12
        console.log("z 출력값:", z);

        x = 9;
        y = 10;
        z = x + y;
        console.log("z 출력값2:", z);
        ```

    - 동일한 변수명으로 재 선언 할 수 있음

      - ```javascript
        var x = 12;
        var y = 15;
        var z = x + y;
        console.log("z 출력값3:", z);
        ```

  - 문제점 ?
    - 이미 선언한 변수에 값도 다시 할 당 할 수 있고(여긴 그나마 문제가 덜됨), 하지만 동일한 변수명을 다시 재 선언함으로 코드의 오류가 발생(공동 작업이나, 원 변수의 의미를 알지 못한다면). 그래서 ES6에서 let, const라는 변수 선언자가 생겼음
  - let
    - 선언한 변수명에 데이터를 다시 할달할 수 있음

      - ```javascript
        let x1 = 5;
        let y1 = 7;
        let z1 = x1 + y1;
        console.log("z1 출력값:", z1);

        x1 = 9;
        y1 = 10;
        z1 = x1 + y1;
        console.log("z1 출력값2:", z1);
        ```

    - 동일한 변수명으로 재 선언 할 수 없음

      - ```javascript
        let x1 = 7; // 동일한 변수명으로 재선언시 에러 발생
        ```

  - const
    - 변수를 선언하는 시점에 값을 반드시 할당해야 함

      - ```javascript
        const PI; // 선언시 값을 할당하지 않아 에러 발생
        const PI = 3.14;
        ```

    - 동일한 변수명을 재 선언 할 수 없으며, 값을 재 할당 할 수도 없음

      - ```javascript
        let PI = 3; // 에러발생
        PI = 3.16; // 에러발생
        ```

## 5. 기본 데이터 타입

- 문자열(String)
  - 쌍따옴표(") 또는 홑따옴표(') 이용 데이터 할당
  
  - ```javascript
    let nameA = "hong-gil-dong";
    let nameB = 'hong-gil-dong';
    let nameC = "hong-'gil'-dong";
    let nameD = 'hong-"gil"-dong';
    ```

- 숫자형(Number)
  - 자바스크립트는 모든 숫자형 데이터를 `64비트 부동소수점`으로 관리
  - 일반적인 형식을 가지는 언어(java, c#)은 다양한 숫자형 데이터 타입을 가짐
  
  - ```javascript
    let num1 = 13; //정수
    let num2 = 2.1; //소수점
    ```

- 참/거짓(Boolean)
  - 2개의 값만 가질 수 있음: 참-true, 거짓-false
  
  - ```javascript
    let num1 = 10;
    let num2 = 5;
    let isBig = num1 >= num2;
    console.log(isBig);
    ```

- undefined
  - 정의되지 않은 혹은 값을 할당하지 않은
  - undefined는 데이터 타입이자 동시에 데이터 값.
  - 실행되는 시점. 런타임 시점에 브라우저 엔진이 자동으로 undefined라는 값을 할당.
  
  - ```javascript
    let a;
    console.log(a);
    ```

- null
  - "없음"을 의미
  - null은 개발자가 의도적으로 할당하는 값
  
  - ```javascript
    // 변수를 선언하는 시점에는 아직 어떤 값이 할당될지 모르는 경우
    // 어떤 데이터 타입으로 할당될지 모르는 경우
    let x = null;
    ``` 

- 메모리를 효율을 위해서 null 사용

  - ```javascript
    let y = "많은양의 문자열 데이터";
    y = null;
    // 가비지 컬렉션 - 더이상 사용하지 않는 메모리를 해제
    ```

### 5.1 Object 타입

- Object Type
  - Object는 데이터를 담을 수 있는 객체
  - 관련 있는 정보를 하나로 묶어서 관리하고 싶을 때 사용
  - 사람 - 이름, 전화번호, 이메일주소, 집주소
  
    - ```javascript
      let name = "홍길동";
      let phone = "010-0000-0000";
      let email = "hong@gmail.com";
      let address = "서울특별시 강남구";
      // 사람, 자동차, 제품과 같이 하나의 값으로 표현할 수 없는 경우에 하나의 변수로 이런 정보를 묶어서 관리할 수 있게 해줌
      // 키(key)와 값(value)을 한 쌍을 갖습니다.

        let person = {
        name: "홍길동",
        phone: "010-0000-0000",
        email: "hong@gmail.com",
        address: "서울특별시 강남구",
      };

      console.log(person);

      // Object에 선언된 특정 키의 값을 읽을 때
      let name = person.name; // 홍길동
      let phone = person.phone; // 010-0000-0000
      let email = person.email; // hong@gmail.com
      let address = person.address; // 서울특별시 강서구 화곡동

      // Object의 특정 키의 값을 변경할 때
      person.address = "부산시 해운대구";
      console.log(person.address);
      console.log(person);

      // Object에 새로운 키-값 추가
      person.gender = "남";
      console.log(person);

      let person2 = {};
      person2.name = "유재석";
      person2.age = 51;
      console.log(person2);

      // Object의 특정 키를 접근하는 방법
      // 1. 변수명.키
      // 2. 변수명["키"] - 키값을 모르는 경우
      console.log(person2.name); // 유재석
      console.log(person2["name"]); // 유재석

      // 동적(실행시점, 런타임시점)으로 Object의 특정 키 값을 가져와야 할 때
      let userSelectedField = "age";
      let userSelectedValue = person2[userSelectedField];
      console.log(userSelectedValue);

      ```

### 5.2 Array 타입

- Array Type
  - 하나 이상의 데이터를 담을 수 있다.
  - 데이터를 담을 때는 순서가 있는 나열 방식
  - 배열은 대괄호[]를 사용해서 데이터를 할당
  - 배열에는 어떤 데이터 타입도 가능
  
  - ```javascript
    let nums = [1, 3, 12, 5, 7];
    let str = ["a", "b", "c", "d"];
    // 배열에는 어떤 데이터 타입도 함께 담을 수 있다.
    let mix = [1, "a", 3, true, {}, []];
    ```
  
- 순서가 존재
  - 순서(순번) 개념을 사용해서 데이터에 접근, 데이터를 가져오고, 데이터 수정
  - 데이터는 순번을 가짐
  - 순번 = index, index 시작 번호는 0부터 시작
  - 배열의 인덱스(index)는 0부터 시작해서 1씩 증가
  
  - ```javascript
    // 인덱스 번호를 사용해서 배열의 특정 요소에 접근할 수 있음.
    console.log(nums[0]); // nums의 첫번째 요소
    console.log(nums[2]); // nums의 세번째 요소

    // 웹 애플리케이션을 이용하고 있는 사용자 목록을 데이터베이스에서 가져옴
    let userList = [
      {
        name: "유재석",
        gender: "남",
        age: 51,
        email: "ryu@gmail.com",
        phone: "010-0000-0000",
      },
      {
        name: "김종국",
        gender: "남",
        age: 47,
        email: "kim@gmail.com",
        phone: "010-0000-0001",
      },
    ];

    let user1 = userList[0];
    console.log(user1.name);
    ```

### 5.3 64 비트 부동소수점

- 부동 소수점
  - 소수점이 고정되어 있지 않기 때문에 지수부와 가수부로 나눠 표현
- JavaScript는 숫자를 저장할 경우 64비트 부동소수점을 사용해서 저장
  - 64비트 부동소수점을 사용해서 계산을할때 오류가 반드시 발생
  - ```64 bit = 1 bit(양수, 음수 표현) + 11 bit(지수부, 자릿수 앞쪽에서 맞춤) + 52 bit(기수부, 자릿수 뒤쪽에서 맞춤)```
  
- ```javascript
  let x = 0.1;
  let y = 0.2;
  let z = x + y;
  console.log(z);
  //0.3이 정상적인 값이지만 64비트 부동소수점으로 계산함으로 끝자리 다르게 표현됨
  //=> 0.30000000000000004

  // 0. x에 대해서 64비트 부동 소수점으로 계산해 보면 아래와 같다.
  // 1. 0.1을 2진수로 나타내면
  //   0.0001100110011001100110011001100110011001100110011001101
  // 2. 1번에 대한 양수 또는 음수를 나타내는 1비트
  //   0
  // 3. 지수부(11 bit()) 계산
  //   0.1의 2진수 값중 정수가 1이 올때까지 소숫점 이동
  //   원래 값 : 0.0001100110011001100110011001100110011001100110011001101
  //   우로 4칸 이동한 값 : 1.100110011001100110011001100110011001100110011001101
  //   2^(n(비트수)-1)-1+m(자릿수이동수) 
  //     = 2^(11비트-1)-1-4칸이동 = 2^(11-1)-1-4 = 1019
  //   1019를 2진수로 계산 = 1111111011 이지만 
  //     11비트를 맞추기 위하여 앞에 0 붙임 = 01111111011
  // 4. 가수부(52 bit) 계산
  //   가수부의 대상 = 우로 4칸 이동한 값 : 1.100110011001100110011001100110011001100110011001101 중
  //     우로 4칸 이동한 값중 소수부분만 사용 100110011001100110011001100110011001100110011001101
  //     52비트 자리수를 위하여 끝에 0을 추가 1001100110011001100110011001100110011001100110011010
  // 5. 결과는
  //    0(음수양수) + 01111111011(지수부) + 1001100110011001100110011001100110011001100110011010(가수부)
  //    = 0011111110111001100110011001100110011001100110011001100110011010

  // 0. y에 대해서 64비트 부동 소주점으로 계산해 보면 아래와 같다.
  // 1. 0.2에 대해서 2진수로 나타내면 = 0.001100110011001100110011001100110011001100110011001101
  // 2. 1번에 대해서 양수 또는 음수 상태 확인
  //      양수 : 0 (음수는 1)
  // 3. 지수부(11 bit)
  //    1이 나올때까지 소숫점 이동 = 우측으로 3칸(-3)
  //      0.001100110011001100110011001100110011001100110011001101 => 1.100110011001100110011001100110011001100110011001101
  //    2^(n-1)-1-m = 2^(11-1)-1-3 = 2^(10)-4 = 1024 - 4 = 1020
  //    1020에 대해서 2진수 = 1111111100
  //    1111111100 는 10 bit임으로 11 bit를 맞추기 위해서 앞에 0를 붙여 비트수 맞춤 = 01111111100
  // 4. 가수부(52 bit)
  //    대상 값은 3번(지수부이 1이 나올때까지 이동한 값의 소수 부분)
  //      100110011001100110011001100110011001100110011001101 (51 bit)
  //      52 bit 자릿수를 위하여 뒤쪽에 0을 붙여 자릿수 맞춤
  //      1001100110011001100110011001100110011001100110011010 (52 bit)
  // 5. 결과는
  //    0(양수) + 01111111100(지수부) + 1001100110011001100110011001100110011001100110011010(가수부)
  //    0011111111001001100110011001100110011001100110011001100110011010
  //
  // 6. 0.0001100110011001100110011001100110011001100110011001101 <- x 0.1에 대한 2진수
  //    0.0011001100110011001100110011001100110011001100110011010 <- y 0.2에 대한 2진수
  //    0.0100110011001100110011001100110011001100110011001100111 <- 0.1 2진수 + 0.2 2진수 더하기
  //    2진수끼리 합을 
  console.log(parseInt("0100110011001100110011001100110011001100110011001100111", 2) * Math.pow(2, -55));
  // => 0.30000000000000004 바로 위의 값
  // => 0.30000000000000004 0.1 + 0.2 값
  ```

- 아주 큰 값을 계산하는 경우 위에서 확인한 듯 작은 오류가 발생한다. 그래서 오류를 잡아주는 라이브러리를 사용하자.
  - [BinNumber](https://mikemcl.github.io/bignumber.js/)
- 16자리 이상의 정수일 때도 문제가 발생
  - 정수에 대해서 최소 ~ 최대의 값을 확인 할 수 있으며, 초과할때는 위의 BigNumber API 사용이 필요

  - ```javascript
    let big = 999999999999999; //15자리 : 정상적으로 할당 됨
    let big2 = 9999999999999999; //16자리 : 오류 발생

    console.log(Number.MAX_SAFE_INTEGER); //9007199254740991
    console.log(Number.MIN_SAFE_INTEGER); //-9007199254740991
    ```

## 6. 연산자(할당, 비교, 산술, 논리, 문자열, 조건삼항)

- 할당 연산자, 비교 연산자, 산술 연산자, 논리 연산자, 문자열 연산자, 조건 삼항 연산자
- [할당 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators#%ED%95%A0%EB%8B%B9_%EC%97%B0%EC%82%B0%EC%9E%90)
  - 우측의 피연산자를 좌측의 연산자에 할당

  - ```javascript
    let x = 1;
    let y = x;
    x = x + y; // 1 + 1 = 2
    x = x - y; // 2 - 1 = 1
    x = x * y; // 1 * 1 = 1
    x = x / y; // 1 / 1 = 1
    // 사칙연산 : +, -, *, /
    // % : 나누고 남은 나머지 값
    
    x = 5;
    y = 2;
    let z = x % y; // 5 / 2의 나머지 = 1

    // ** : 제곱근
    x = 3;
    y = 2;
    x = x ** y; //3^2=9

    // 복합 할당 연산자
    x += y; //x = x + y
    x -= y; //x = x - y
    x *= y; //x = x * y
    x /= y; //x = x / y
    x %= y; //x = x % y
    ```

- [비교 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators#%EA%B4%80%EA%B3%84_%EC%97%B0%EC%82%B0%EC%9E%90)
  - 값이나 데이터를 비교하기 위함
  
  - ```javascript
    let x = 3;
    let y = 4;
    console.log(x == y); //false

    x = 3;
    y = "3";
    console.log(x == y); //true, javascript의 장점이자 단점, 데이터 타입 비교 없이 값만 비교함 
    console.log(x === y); //false, 데이터 타입 및 값 모두 비교
    console.log(x != y); //false, 값만 비교
    console.log(x !== y); //ttrue, 데이터타입 및 값 비교

    x = 5;
    y = 2;
    console.log(x > y); //true
    y = 5;
    console.log(x >= y); //true
    console.log(x < y); //false
    console.log(x <= y); //true
    ```
    
- [산술 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators#%EC%82%B0%EC%88%A0_%EC%97%B0%EC%82%B0%EC%9E%90)
  - 증가연산자(++), 감소연산자(--), 단항 부정 연산자, 숫자화연산자
    - 증가연산자는 ++ 기호를 사용. 1를 증가
    - 감소연산자는 -- 기호를 사용. 1을 감소
    - 단항 부정 연산자는 피연산자의 값의 부호가 바뀐다.
    - 숫자화연산자는 숫자가 아닌 문자/boolean 값을 숫자로 변환하는 시도를 함 (+)
  
  - ```javascript
    // 증가연산자
    let x = 5;
    y = x++; //할당을 한 후 증가해라
    console.log(y); //5
    console.log(x); //6
    x = 5;
    y = ++x; //할당전 증가해라
    console.log(y); //6
    console.log(x); //6

    // 감소연산자
    x = 5;
    y = x--; //할당을 한 후 감소
    console.log(y); //5
    console.log(x); //4
    x = 5;
    y = --x;
    console.log(y); //4
    console.log(x); //4

    // 단항 부정 연산자
    x = -3;
    console.log(x); //-3
    console.log(-x); //3

    // 숫자화 연산자 (수화가 가능한 값의 경우 가능)
    x = "3";
    y = +x;
    console.log(y); //3(숫자)
    console.log(y === x); //false
    
    console.log(+true); //1
    console.log(+false); //0

    // 논리 연산자
    // 조건을 여러가지를 만족하는 연산자
    // AND : &&
    // OR : ||
    let o = true && false;
    console.log(o); //false

    o = (3 > 2) && (4 > 7);
    console.log(o); //false
    o = (3 > 2) && (8 > 7);
    console.log(o); //true

    o = true || false;
    console.log(o); //true
    o = (3 > 2) || (4 > 7);
    console.log(o); //true
    o = (2 > 3) || (7 > 8);
    console.log(o); //false
    ```
    
- 문자열 연산자
  - 두개의 문자열을 합침
  
  - ```javascript
    let firstName = "Hong";
    let lastName = "gil-dong";
    lst fullName = firstName + lastName;
    console.log(fullName); //Honggil-dong";
    ```
    
- [조건 삼항 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators#%EC%A1%B0%EA%B1%B4%EB%B6%80%EC%82%BC%ED%95%AD_%EC%97%B0%EC%82%B0%EC%9E%90)
  - 비교 연산을 하면서 ?를 사용하여 true일때 false일때 값을 연산할 수 있음
  
  - ```javascript
    let age = 16;
    let isAudult = age >= 20 ? "성인" : "미성년자";
    console.log(isAudult); //미성년자

    let point = 88;
    let grade = point >= 90 ? "A" : point >= 80 ? "B" : point >= 70 ? "C" : "D";
    console.log(grade); //B
    ```

## 7. 조건문

- [조건문](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks/conditionals)
- [if...else](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/if...else)

  - ```javascript
    let busFare = 0;
    let age = 70;

    if (age < 8) {
      busFare = 0;
    } else if (age >= 8 && age < 14) {
      busFare = 450;
    } else if (age >= 14 && age < 20) {
      busFare = 700;
    } else if (age >= 20 && age < 70) {
      busFare = 1000;
    } else {
      // 70보다 같거나 큰 경우
      busFare = 0;
    }

    console.log("버스요금:", busFare);

    if (age < 8) {
      busFare = 0;
    } else if (age < 14) {
      busFare = 450;
    } else if (age < 20) {
      busFare = 700;
    } else if (age < 70) {
      busFare = 1000;
    } else {
      busFare = 0;
    }

    // 다음과 같은 값은 조건식에서 모두 것지(false)로 취급이 됨.
    // false
    // undefined
    // null
    // 0
    // "" 비어있는 문자열
    let x;
    x = null;
    x = 0;
    x = "";
    if (x) {
    } else {
      console.log("else구문이 실행");
    }
    ```

- [switch](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/switch)

  - ```javascript
    // Date 객체 - 날짜와 시간과 관련된 객체
    const d = new Date();
    const day = d.getDay(); // 코드가 실행되는 시점의 요일. 요일 값을 숫자로 알려줌.
    console.log(day);
    // 0 - 일요일, 1 - 월요일, 2 - 화요일, 3 - 수요일, 4 - 목요일, 5 - 금요일, 6 - 토요일

    // 상수값 비교, 비교 연산자를 가질 수 없음.
    switch (day) {
      case 0:
        dayName = "일요일";
        break;
      case 1:
        dayName = "월요일";
        break;
      case 2:
        dayName = "화요일";
        break;
      case 3:
        dayName = "수요일";
        break;
      case 4:
        dayName = "목요일";
        break;
      case 5:
        dayName = "금요일";
        break;
      case 6:
        dayName = "토요일";
        break;
      default:
        break;
    }

    console.log(dayName);

    let dayNames = [
      "일요일",
      "월요일",
      "화요일",
      "수요일",
      "목요일",
      "금요일",
      "토요일",
    ];
    // 0 - 일요일, 1 - 월요일, 2 - 화요일, 3 - 수요일, 4 - 목요일, 5 - 금요일, 6 - 토요일
    console.log(dayNames[day]);
    ```

## 8. 반복문

- 코드 블럭을 원하는 횟수만큼 반복 실행되게 함
- 반복문의 종류
  - for, for...in, for...of, forEach, while(do-while)
  - [for](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for)
    - initialization, condition, final-expression으로 구분
    - continue, break 

    - ```javascript
      for ([initialization]; [condition]; [final-expression]){
        statement;
      }

      for (var i = 0; i < 9; i++) {
        console.log(i);
        // 기타 등등
      }
      ```

  - [for...in](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in)
    - `객체의 반복에 사용`
    - 속성(배열, 객체)을 포함한 객체나 열거 가능한 속성에 대해서 반복
    - 객체의 모든 열거가능한 속성에 대해서 반복

    - ```javascript
      var obj = {
        a: 1,
        b: 2,
        c: 3
      };
      for (var item of obj) {
          console.log(item);// a, b, c
      }

      //배열도 object 타입으로 인식해서 결과는 출력되나 배열의 index가 출력됨.
      var arr = [1, 2, 3];
      for (var item in arr) {
        console.log(item) // 0, 1, 2
      }
      ```
   
  - [for...of](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...of)
    - `배열의 반복에 사용`
    - 컬렉션 전용 반복
    - 모든 객체보다는 [System.iterator] 속성이 있는 모든 컬렉션 요소에 대해 반복

    - ```javascript
      var arr = [1, 2, 3];
      for (var item of arr) {
        console.log(item); // 1, 2, 3
      }

      var obj = {
        a: 1,
        b: 2,
        c: 3
      };
      for (var item of obj) {
          console.log(item);
      }
      //Uncaught TypeError: obj is not iterable
      ```

  - [forEach](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
    - 배열 객체의 함수로 파라메터로 함수를 정의해서 사용 가능

    - ```javascript
      let brands = ["A", "B', "C", "D", "E"];
      brands.forEach(function (item, index) {
          console.log(item);
      });
      ```

  - [while](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/while)
    - 조건문이 참일 때 실행되는 반복문
    - 조건은 문장안이 실행되기 전에 참, 거짓을 판단
    - 몇번을 반복해야 할지 알 수 없을때 많이 사용
    - do { 코드블럭 } while (조건문)
      - 무조건 한번은 코드 블럭을 실행하고, 조건문을 체크

## 9. 함수

- 반복적인 기능, 재사용 가능한 코드 묶음
- 특정 작업을 여러번 반복해야하는 경우 해당 작업을 재사용 가능한 구조로 만들게 되면 중복 작업을 피할 수 있고 이미 만들어 놓은 기능을 사용함으로 쉽게 코드를 짤 수 잇다

- [함수 선언식](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/function)
  - 함수 이름을 만들어 사용.
  - 함수 선언식 : 메소드라고도 함, function 키워드 사용
  - 함수는 공통적인 기능을 위해 많이 사용하고 공통 함수 담당이 만들고 유지보수하고 분리해서 개발하는 경향이 실무에 많다.

  - ```javascript
    console.log(plus(9, 12)); // 인터프리터 방식이 아니라 사용 가능

    function plus(num1, num2) {
      // 정의할 코드 블록, 함수 기능
      let sum = num1 + num2;
      return sum; // 함수를 호출한 곳으로 반환
    }

    let sum1 = plus(3, 5); // 8
    console.log(sum1);

    let sum2 = plus(7, 9);
    console.log(sum2);
    ```

  - /** 엔터*/
    - 함수의 리마크 자동 생성

- [함수 표현식](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/function)
  - 변수를 선언해서 사용하는 것처럼 변수에 함수을 할당
  - const sum = function(num1, num2) { return num1+num2; }

  - 실행의 측면에서 선언식, 표현식 차이가 존재
    - `선언식은 인터프리트 방식 아님`(자바 엔진이 함수 선언식부터 해석하고 가지고 잇음)
    - `표현식(변수)은 인터프리트 방식`

  - ```javascript
    console.log(sum(5, 9)); // 인터프리터 방식으로 오류 발생

    const sum = function (num1, num2) {
      return num1 + num2;
    };

    console.log(sum(5, 9));
    ```

- [function 생성자 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function#function_인스턴스)
  - 자바스크립트 내장 함수 function
  - 문자열로 파라미터, 코드블럭 순서대로 넣어 만듬
  - const add = new Function(“num1”, “num2”, “return num1+num2”); 마지막이 코드블럭, 앞은 파라미터임

  - ```javascript
    const add = new Function("num1", "num2", "return num1 + num2");
    console.log(add(21, 27));

    function calculator(num1, num2, operator) {
      if (operator === "+") {
        return num1 + num2;
      } else if (operator === "-") {
        return num1 - num2;
      } else if (operator === "*") {
        return num1 * num2;
      } else if (operator === "/") {
        return num1 / num2;
      }
    }
    const operator = "+";
    const cal = new Function(
      "num1",
      "num2",
      "return num1 " + operator + " num2"
    );
    ```

- [화살표 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
  - (실무에서 가장 많이 사용) 나중이 배운다

## 10. 주요 객체와 내장 함수

### 10.1 String

- [string](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)
  - 문자열은 텍스트 형태로 표현될 수있는 데이터를 보관하는 데 유용합니다. 문자열에서 가장 많이 사용되는 작업들은 문자열의 길이를 확인하는 `(length)`, 문자열을 생성하고 연결하는 + 와 += `문자열 연산자`, `서브문자열(substring)`이 있는지 확인하고, 있으면 위치를 확인하는 `indexOf()` 메서드, `서브문자열(substring)`을 추출해내는 substring() 메서드가 존재

- 관련 내장 함수 및 속성
  - [indexOf()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)
    - 그 문자열이 시작되는 인덱스 번호를 반환
  - [lastIndexOf()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf)
    - 파라메터 : 찾고자 하는 문자열, 시작할 인덱스 번호
    - 마지막 인덱스 번호

  - 문자열을 잘라내는 내장 함수 (세밀하게 차이점이 존재 한다.)
    - [slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
      - (시작위치, 종료위치) 파라메터로 문자열을 잘라 반환
      - 시작위치만 파라메터만 주면, 종료 위치는 자동으로 끝으로 간다.
      - 값은 뒤에서 부터 시작
      - 문자열을 뒤에서부터 찾을때 가장 많이 사용
    - [substring()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/substring)
      - (시작위치, 종료위치) 파라메터로 문자열 잘라 반환
      - 음수값을 가질 수 없다 !!
    - [substr()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/substr)
      - (시작위치, 잘라낼길이) 파라메터로 문자열 잘라 반환
      - 잘라낼 길이를 정확하게 아는 경우 사용
  - [replace()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
    - (문자열1, 문자열2) - 문자열에서 문자열1을 찾아서 문자열2로 교체
    - 발견되는 첫번째 문자열만 변경함
    - 정규식을 통하여 전체 문자열 통제 가능

  - toXXXCase()
    - [toUpperCase()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) - 모든 알파벳을 대문자로 변경
    - [toLowerCase()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase) - 모든 알파멧을 소문자로 변경
    - 검색에 대한 일관성(대/소문자)을 위하여 가장 많이 사용
  - [concat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/concat) - 여러 문자열을 하나로 결합
  - [trim()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/Trim) - 문자열의 앞/뒤 공백 제거

  - [padStart()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) - 두개의 파라메터를 받아서 첫번째 파라메터는 "길이", 두번째 파라메터는 "채울 문자"
    - "ST" -> 4, "A" -> AAST
    - 첫번째 파라메터로 전달 받은 길이만큼 문자열의 앞에 두번째 파라메터로 전달 받은 문자로 채움
    - [padEnd()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd)
      - padStart() 와 동일하나 문자열의 뒤에서 처리함

  - [charAt()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)
    - 첫번째 파라메터 - 인덱스 번호
    - 문자열에서 인덱스 번호에 해당하는 문자 하나를 반환
  - [charCodeAt()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)
    - 인덱스번호에 맞는 하나의 문자를 반환
    - 문자를 유니코드로 변환해서 반환. 
  - [split()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/split)
    - 파라메터로 전달 받은 문자열로 앞뒤로 분리하여 배열로 반환
    - let to = "a@a.com, b@b.com, c@c.com";
    - let tags = "#A#B#C";

  - [startsWith()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith) - 파라메터로 전달받은 문자열로 시작하는지를 확인 후 boolean으로 반환
  - [endsWith()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith) - 파라메터로 전달받은 문자열로 끝나는지 확인 후 boolean으로 반환

  - 유니코드 : 전 세계 모든 문자를 컴퓨터에서 일관되게 표현하고 다룰 수 있게 설계된 산업 표준
    - 일관된 산업 표준으로 만드는 것을 "인코딩"이라고 하는데 인코딩의 방식에는 수없이 많은 방법이 존재 한다. (euc-kr, iso ... )
    - 인코딩 - utf-8이 가장 대표적인 인코딩 방식

### 10.2 Number

- [Number](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number)
- `Number` 는 `37`이나 `-9.25`와 같은 숫자를 표현하고 다룰 때 사용하는 원시 래퍼 객체
- 관련 내장 함수 및 속성
  - [toString()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toString)
    - 문자형 데이터 타입으로 변경
  - [toExponential()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toExponential)
    - 지수표기법으로 반환
    - 과학, 공학에서 큰 숫자 사용
  - [toFixed()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)
    - 소수점 자릿수 표기

    - ```javascript
      let x = 10.656;
      console.log(x.toFixed(0)); // 11
      console.log(x.toFixed(1)); // 10.7
      console.log(x.toFixed(2)); // 10.66
      console.log(x.toFixed(4)); // 10.6560
      ```

  - [toPrecision()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision)
    - 정수 + 소수를 포함하여 전체 자릿수 표기

    - ```javascript
      let x = 10.656;
      console.log(x.toPrecision(2)); // 11
      console.log(x.toPrecision(3)); // 10.7
      ```

  - [parseInt()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/parseInt)
    - 문자를 정수로 변환

    - ```javascript
      console.log(parseInt("3")); // 숫자 3
      console.log(parseInt("12.33")); // 숫자 12
      console.log(parseInt("12.77")); // 숫자 12
      console.log(parseInt("10 20 30")); // 숫자 10
      console.log(parseInt("10 years")); // 숫자 10
      console.log(parseInt("10살")); // 숫자 10
      ```

  - 사용자로부터 입력 받은 값(수)의 연산
    - 사용자로부터 입력된 값(수)을 연산하는 경우 사용
    - 사용자로 입력받은 값은 실제로 문자(string) 임
    - 숫사 연산을 위해서는 문자를 숫자로 변환하여 연산 필요
  - [parseFloat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/parseFloat)
    - 부동소수점으로 반환 
  - 값의 유효범위 확인
    - [MAX_SAFE_INTEGER](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER)

      - ```javascript
        console.log(Number.MAX_SAFE_INTEGER);
        ```

    - [MIN_SAFE_INTEGER](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/MIN_SAFE_INTEGER)

      - ```javascript
        console.log(Number.MIN_SAFE_INTEGER);
        ```

### 10.3 Array

- JavaScript [Array](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array) 클래스는 리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체입니다.
- 배열은 리스트와 비슷한 객체로서 순회와 변형 작업을 수행하는 메서드를 갖음
- JavaScript 배열은 길이도, 각 요소의 자료형도 고정되어 있지 않고, 배열의 길이가 언제든지 늘어나거나 줄어들 수 있고 데이터를 연속적이지 않은 곳에 저장할 수 있으므로, JavaScript 배열은 밀집성을 보장하지 않음
- 관련 내장 함수 및 속성
  - [toString()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)
    - 문자열 객체로 변환하여 반환

    - ```javascript
      let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
      console.log(brands.toString());
      // Output:
      // 애플,구글,아마존,마이크로소프트,메타
      ```

  - [join()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
    - 파라미터의 문자가 요소 사이 삽입되어 하나의 문자로 반환
    - 배열을 이용해서 태그에 바인딩 샘플(문자열 더하기 vs 배열 push & join, 버튼 테이블 태그 추가하여 샘플 작성)

    - ```javascript
      console.log(brands.join(" * "));
      // Output:
      // 애플 * 구글 * 아마존 * 마이크로소프트 * 메타
      console.log(brands.join(""));
      // Output:
      // 애플구글아마존마이크로소프트메타
      ```

  - [push()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
    - 파라미터의 문자를 마지막 요소로 추가

    - ```html
      <button onclick="doSearch();">조회</button>
      <table>
        <thead>
          <th>음료</th>
          <th>가격</th>
        </thead>
        <tbody id="tbBody"></tbody>
      </table>
      ```

    - ```javascript
      function doSearch() {
        const drinkList = [
          {
            name: "오렌지",
            price: 1000,
          },
          {
            name: "파워레이드",
            price: 1400,
          },
          {
            name: "커피",
            price: 700,
          },
          {
            name: "보리음료",
            price: 1200,
          },
          {
            name: "코카콜라",
            price: 1000,
          },
        ];

        // push()
        let trTags = [];
        for (const drink of drinkList) {
          trTags.push("<tr>");
          trTags.push("<td>" + drink.name + "</td>");
          trTags.push("<td>" + drink.price + "</td>");
          trTags.push("</tr>");
        }

        console.log(trTags.join(""));
        document.getElementById("tbBody").innerHTML = trTags;
      }
      ```

  - [unshift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
    - 파라미터의 문자를 첫번째 요소로 추가
    - select의 옵션추가 샘플
    - push가 일반적이나 태그 밖으로 뺄때는 unshift가 더 효율적이다

    - ```javascript
      let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
      brands.unshift("삼성전자");
      // Output:
      // 6
      console.log(brands);
      // Output:
      // Array(6) [ "삼성전자", "애플", "구글", "아마존", "마이크로소프트", "메타" ]
      ```

    - ```javascript
      function loadDrinkType() {
        const types = [
          { text: "이온음료", code: "A" },
          { text: "커피", code: "B" },
          { text: "탄산음료", code: "C" },
        ];

        const h = [];
        for (const type of types) {
          h.push(
            '<option value="' + type.code + '">' + type.text + "</option>"
          );
        }

        return h;
      }

      const selDrinkType = loadDrinkType();
      selDrinkType.unshift('<option value=""></option>');
      document.getElementById("selDrinkType").innerHTML = selDrinkType.join("");
      ```

  - [pop()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) / 
    - 마지막 요소 제거 후 반환

    - ```javascript
      let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
      console.log(brands.pop());
      // Output: 
      // 메타
      console.log(brands);
      // Output: 
      // Array(4) [ "애플", "구글", "아마존", "마이크로소프트" ]
      ```

  - [shift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
    - 첫번째 요소 제거 후 반환
    - shift는 메시지큐 처리에 많이 사용

    - ```javascript
      const array1 = [1, 2, 3];
      const firstElement = array1.shift();

      console.log(array1);
      // Output: 
      // Array [2, 3]

      console.log(firstElement);
      // output:
      // 1
      ```

  - [splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
    - 특정 위치에 요소 추가, 추가시 삭제도 가능
    - 첫번째 파라미터 - 새로운 요소를 추가할 인덱스 번호
    - 두번째 파라미터 - 요소를 추가하기전에 삭제할 요소 수
    - 나머지 파라미터 - 추가할 요소

    - ```javascript
      let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
      brands.splice(1, 0, "개발자의품격", "더그레잇");
      console.log(brands);
      // Output:
      // Array(7) [ "애플", "개발자의품격", "더그레잇", "구글", "아마존", "마이크로소프트", "메타" ]
      ```

  - [concat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
    - 2개 이상의 배열 결합

    - ```javascript
      let arr1 = ["A", "B"];
      let arr2 = ["C", "D"];
      let arr3 = ["E", "F", "G"];
      let arr4 = arr1.concat(arr2, arr3);
      console.log(arr4);
      // Output:
      // Array(7) [ "A", "B", "C", "D", "E", "F", "G" ]
      ```

  - [slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
    -요소를 잘라내서 배열 타입으로 반환

    - ```javascript
      console.log(arr4.slice(1, 2));
      // Output:
      // Array [ "B" ]
      ```

  - [sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
    - 요소를 정렬
    - 문자열 정렬, 숫자 정렬 샘플
    - 숫자정열시 함수에서 양수는 바꿈, 음수는 바꾸지 않은, 0 같음
    - 배열내 객체의 정렬 샘플(숫자, 문자의 경우 차이점 이해해야함)

    - ```javascript
      let points = [40, 100, 1, 5, 25, 10];
      console.log(points.sort());
      // Output:
      // Array(6) [ 1, 10, 100, 25, 40, 5 ]

      const ascPoints = points.sort(function (a, b) {
        // a - 40, b-100
        // [40, 100, 1, 5, 25, 10]
        // a - 100, b - 1
        // [40, 1, 100, 5, 25, 10]
        // a - 100, b -5
        // [40, 1, 5, 100, 25, 10]
        // a - 100, b - 25
        // [40, 1, 5, 25, 100, 10]
        // [1, 5, 10, 25, 40, 100]
        // if (a > b) return 1;
        // else if (a < b) return -1;
        // else 0;
        return a - b;
      });
      console.log(ascPoints);

      const descPoints = points.sort(function (a, b) {
        return b - a;
      });
      console.log(descPoints);

      let drinkList = [
        {
          name: "오렌지",
          price: 1000,
        },
        {
          name: "파워레이드",
          price: 1400,
        },
        {
          name: "커피",
          price: 700,
        },
        {
          name: "보리음료",
          price: 1200,
        },
        {
          name: "코카콜라",
          price: 1000,
        },
      ];

      const userSortKey = "name";

      const ascDrinkList = drinkList.sort(function (a, b) {
        if (a[userSortKey] > b[userSortKey]) return 1;
        else if (a[userSortKey] < b[userSortKey]) return -1;
        else 0;
      });
      console.log(ascDrinkList);
      ```

  - [filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
    - 특정 조건의 요소를 찾고 배열로 반환
    - 필터 함수 사용 샘플

    - ```javascript
      let drinkList = [
        {
          name: "오렌지",
          price: 1000,
        },
        {
          name: "파워레이드",
          price: 1400,
        },
        {
          name: "커피",
          price: 700,
        },
        {
          name: "보리음료",
          price: 1200,
        },
        {
          name: "코카콜라",
          price: 1000,
        },
      ];

      let availableProduct = [];
      const inputCoin = 1000;

      availableProduct = drinkList.filter(function (drink) {
        return drink.price <= inputCoin;
      });

      console.log(availableProduct);
      // Output:
      // Array(3) [ {…}, {…}, {…} ]
      //  0: Object { name: "오렌지", price: 1000 }
      //  1: Object { name: "커피", price: 700 }
      //  2: Object { name: "코카콜라", price: 1000 }
      ```

  - [map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
    - 배열의 요소가 객체의 경우(key-value), 새로운 객체로 변경 후 배열 반환

    - ```javascript
      let userList = [
        {
          firstName: "재석",
          lastName: "유",
          email: "ryu@gmail.com",
        },
        {
          firstName: "종국",
          lastName: "김",
          email: "kim@gmail.com",
        },
        {
          firstName: "지효",
          lastName: "송",
          email: "song@gmail.com",
        },
      ];

      let newUserList = userList.map(function (user) {
        return {
          fullName: user.lastName + user.firstName,
          email: user.email,
        };
      });

      console.log(newUserList);
      // Output:
      // Array(3) [ {…}, {…}, {…} ]
      //  0: Object { fullName: "유재석", email: "ryu@gmail.com" }
      //  1: Object { fullName: "김종국", email: "kim@gmail.com" }
      //  2: Object { fullName: "송지효", email: "song@gmail.com" }
      ```

  - [reduce()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
    - 요소의 크기만큼 callback 호출(재귀 호출)하면서 누적된 값을 출력
    
    - ```javascript
      points = [40, 100, 1, 5, 25, 10];

      let sum = points.reduce(function (accumulator, currentValue) {
        return accumulator + currentValue;
      }, 0); 
      
      console.log(sum);

      drinkList = [
        {
          name: "오렌지",
          price: 1000,
        },
        {
          name: "파워레이드",
          price: 1400,
        },
        {
          name: "커피",
          price: 700,
        },
        {
          name: "보리음료",
          price: 1200,
        },
        {
          name: "코카콜라",
          price: 1000,
        },
      ];

      let drinkTotal = drinkList.reduce(function (total, drink) {
        return total + drink.price;
      }, 0);
      console.log(drinkTotal);

      userList = [
        {
          firstName: "재석",
          lastName: "유",
          email: "ryu@gmail.com",
        },
        {
          firstName: "종국",
          lastName: "김",
          email: "kim@gmail.com",
        },
        {
          firstName: "지효",
          lastName: "송",
          email: "song@gmail.com",
        },
        {
          firstName: "가네",
          lastName: "김",
          email: "kim2@gmail.com",
        },
      ];

      let kims = userList.reduce(function (users, user) {
        if (user.lastName === "김") {
          users.push(user);
        }

        return users;
      }, []);

      console.log(kims);
      ```

### 10.4 Date

### 10.5 Set

### 10.6 Map

### 10.7 Math

### 10.8 JSON

### 10.9 window

## 11. Reference

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)