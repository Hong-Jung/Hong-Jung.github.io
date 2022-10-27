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
    - ```javasscript var userName = "walter";```
  - [스네이크 표기법(snake_case)](https://ko.wikipedia.org/wiki/%EC%8A%A4%EB%84%A4%EC%9D%B4%ED%81%AC_%ED%91%9C%EA%B8%B0%EB%B2%95)
    - ```javasscript var user_name = "walter";```
  - 파스칼 표기법(PascalCase)
    - ```javasscript var UserName = "walter";```
  - [헝가리언 표기법(데이터타입의 약어사용)](https://ko.wikipedia.org/wiki/%ED%97%9D%EA%B0%80%EB%A6%AC%EC%95%88_%ED%91%9C%EA%B8%B0%EB%B2%95)
    - ```javasscript var strUserName = "walter";```
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

## 7. 조건문

## 8. 반복문

## 9. 함수

## 10. 주요 객체와 내장 함수

### 10.1 String

### 10.2 Number

### 10.3 Array

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