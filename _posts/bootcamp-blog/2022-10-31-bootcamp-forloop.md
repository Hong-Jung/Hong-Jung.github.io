---
title:  "JavaScript in Loop Statement."
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, VariableDeclaration]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-31
last_modified_at: 2022-10-31
---

# What is ***Loop(반복) Statement(문)*** in JavaScript ?

## 0. Index

- [What is ***Loop(반복) Statement(문)*** in JavaScript ?](#what-is-loop반복-statement문-in-javascript-)
  - [0. Index](#0-index)
  - [1. Introduction](#1-introduction)
    - [1.1 반복문 이란 ?](#11-반복문-이란-)
    - [1.2 반복문이 왜 필요할까 ?](#12-반복문이-왜-필요할까-)
    - [1.3 반복문이 종류는 ?](#13-반복문이-종류는-)
  - [2. Body](#2-body)
    - [2.1 for](#21-for)
    - [2.2 for...in](#22-forin)
    - [2.3 for...of](#23-forof)
    - [2.4 forEach](#24-foreach)
  - [3. Conclusion](#3-conclusion)
  - [4. Reference](#4-reference)

## 1. Introduction 

- 블로그에서 다루는 내용
  - 반복문이 *무엇*인지, *왜* 사용하는지 마지막으로 *종류*는 몇가지가 있으며, 각 종류별 사용 샘플 및 특이점에 대해서 알아본다.

### 1.1 반복문 이란 ?

- JavaScript에서 `조건`에 따라 `반복`되는 작업을 수행하는 데 사용되며, 조건은 일반적으로 `true` 또는 `false를` 반환한다. `반복은 정의된 조건이 false를 반환할 때까지 계속 실행` 된다.

### 1.2 반복문이 왜 필요할까 ?

- 프로그램밍을 통한 코드작성의 가장 기본적인 목적은 반복을 줄이는 해법을 고민해서 탄생하지 않았나? 생각한다.
- 일상적인 생활이나, 시스템 개발에 있어 반복적으로 이루어지는 경우가 생각보다 많다. (다음은 심플한 사무직의 출근 후 제일 우선 업무의 샘플이다)
  - 아침 사무실에 출근하면 지난밤 퇴근 이후 수신된 메일 중 특정 제목의 메일을 필터링하여 모든 첨부 파일을 로컬 컴퓨터로 저장
    - 반복요인
      - 동일한 제목의 메일 제목을 하나하나 반복하며 검색
      - 메일의 첨부 파일을 로컬 컴퓨터로 저장
  - 저장된 파일을 엑셀 파일로 오픈하여, 병합하여 하나의 써머라이즈 엑셀 파일을 생성
    - 반복요인
      - 파일 하나씩 오픈하여 내용을 하나의 써머라이즈 파일에 복사&붙여넣기
  - 써머라이즈 엑셀 파일을 다시 행과 열에 따른 산술식을 적용
    - 반복요인
      - 행과 열의 특정 수식(더하기, 평균 등)을 적용하여 계산
  - 써머라이즈된 엑셀 파일을 관련부서에 메일로 회람 
    - 반복요인
      - 써머라이즈 파일을 첨부하여 관련부서(10개)를 수신처로 메일을 송부
- 위와 같이 우리가 일상적으로 반복적인 작업을 많이 수행하고 있으며, 이번 블로그는 순수 반복 작업을 JavaScript에서 어떤 문법으로 처리하는지 중점을 두며, 모든 학습을 마친다면 상단의 반복 업무에 대해서 자동화 시스템을 개발할 수 있을 것이다.

### 1.3 반복문이 종류는 ?

- `for`, `for...in`, `for...of`, `forEach`, `while`, `do...while`

## 2. Body

### 2.1 for

- for 루프는 세 개의 선택적 표현식과 그 뒤에 오는 코드 블록으로 구성
  
  - ```javascript
    // syntax
    for ([initialization]; [condition]; [finalExpression]) {
      // statement
    }
    ```

  - `initialization`
    - 첫 번째 반복이 실행되기 전에 실행되며, 일반적으로 카운터를 만드는 데 사용
  - `condition`
    - 반복이 실행되기 전에 매번 확인. true로 평가되면 반복의 명령문이나 코드가 실행됨. false로 평가되면 반복이 중지. 생략하면 자동으로 true로 평가됨.
  - `finalExpression`
    - 각 반복 후에 실행. 일반적으로 카운터를 증가 또는 감소에 사용
- for 반복은 일반적으로 코드를 정해진 횟수만큼 실행하는 데 사용. 
- 조건식이 false로 평가되기 전에 break를 사용하여 반복을 일찍 종료할 수 있음

- ```javascript
  // sample code
  for (let i = 0; i < 9; i++) {
    console.log(i);
  }

  // Output:
  // 0
  // 1
  // 2
  // 3
  // 4
  // 5
  // 6
  // 7
  // 8
  ```

- 조건이 false가 되기 전에 for 루프를 종료하려면 break를 사용

- ```javascript
  for (let i = 1; i < 10; i += 2) {
    if (i === 7) {
      break;
    }
    console.log('Total elephants: ' + i);
  }

  // Output:
  // Total elephants: 1
  // Total elephants: 3
  // Total elephants: 5
  ```

- 배열의 길이 초과하는 경우에 대해서 알아보자
  - 배열을 반복할 때 실수로 배열의 길이를 초과하기 쉽다.
  - 예를 들어, 반복은 3개의 요소만 있는 배열의 4번째 요소를 참조하려고 할 수 있다.
  
  - ```javascript
    const arr = [ 1, 2, 3 ];

    for (let i = 0; i <= arr.length; i++) {
      console.log(arr[i]);
    }

    // Output:
    // 1
    // 2
    // 3
    // undefined

    // 수정하는 2가지 방법
    // 1. 조건을 i < arr.length 변경
    // 2. i <= arr.length - 1 설정
    ```

### 2.2 for...in

- for...in 반복은 `객체`의 속성을 반복
- 각 `속성`에 대해 `코드 블록`의 코드가 실행
  
- ```javascript
  // syntax
  for (property in object) {
    // code
  }
  ```

- ```javascript
  const capitals = {
    a: "Athens",
    b: "Belgrade",
    c: "Cairo"
  };

  for (let key in capitals) {
    console.log(key + ": " + capitals[key]);
  }

  // Output:
  // a: Athens
  // b: Belgrade
  // c: Cairo
  ```

### 2.3 for...of

- `배열`과 `Set` 및 `Map과` 같은 특수 컬렉션 유형을 포함한 다양한 유형의 반복 가능한 값을 반복
- `반복 가능한 객체`의 `각 값`에 대해 코드 블록의 코드가 실행

- ```javascript
  // syntax
  for (variable of object) {
    // code
  }
  ```

- ```javascript
  const arr = [ "Fred", "Tom", "Bob" ];

  for (let i of arr) {
    console.log(i);
  }

  // Output:
  // Fred
  // Tom
  // Bob
  ```

### 2.4 forEach

- 배열 객체의 함수로서 사용
- 콜백 함수(callback function)와 다음의 3가지 매개변수(parameter)와 함께 전달
  - Value (명명된 매개변수) - 처리할 현재 요소
  - Index (선택적 매개변수) - 처리할 현재 요소의 인덱스
  - Array (선택적 매개변수) - forEach 메서드를 호출한 배열

- ```javascript
  const numbers = [1, 2, 3, 4, 5];
  
  numbers.forEach(function() {
      // code
  });

  //Value (명명된 매개변수) - 처리할 현재 요소
  numbers.forEach(function(number) {
      console.log(number);
  });
  // Output:
  //1
  //2
  //3
  //4
  //5

  //Index (선택적 매개변수) - 처리할 현재 요소의 인덱스
  numbers.forEach(function(number, index) {
      console.log('Index: ' + index + ' Value: ' + number);
  });
  // Output:
  //Index: 0 Value: 1
  //Index: 1 Value: 2
  //Index: 2 Value: 3
  //Index: 3 Value: 4
  //Index: 4 Value: 5

  //Array (선택적 매개변수) - forEach 메서드를 호출한 배열
  numbers.forEach(function(number, index, array) {
      console.log(array);
  });
  // Output:
  //(5) [1, 2, 3, 4, 5]
  //(5) [1, 2, 3, 4, 5]
  //(5) [1, 2, 3, 4, 5]
  //(5) [1, 2, 3, 4, 5]
  //(5) [1, 2, 3, 4, 5]
  ```

### 2.5 while(do...while)

- 조건을 평가하는 것으로 시작
- 조건이 true로 평가되면 코드 블록의 코드가 실행되고, 조건이 false로 평가되면 코드 블록의 코드가 실행되지 않고 루프가 종료

- ```javascript
  // syntax
  while(true) {
    // code
  }
  ```

- ```javascript
  let i = 1;

  while (i < 10) {
    console.log(i);
    i++;
  }

  // Output:
  // 1
  // 2
  // 3
  // 4
  // 5
  // 6
  // 7
  // 8
  // 9
  ```

- do...while 
  - 조건은 반복이 실행되기 전에 시되는 것이 아니라, 반복이 끝날 때 확인
  - 즉, 조건 표현식이 false 이더라도, 코드 블럭의 코드는 최소한 한 번은 실행

  - ```javascript
    // syntax
    do {
      // statement
    } while (true)
    ```

  - ```javascript
    let i = 1;

    do {
      console.log(i);
      i++;
    } while (i < 10);

    // Output:
    // 1
    // 2
    // 3
    // 4
    // 5
    // 6
    // 7
    // 8
    // 9

    const myArray = [];
    let i = 10;

    do {
      myArray.push(i);
      i++;
    } while (i < 10);

    console.log(myArray);

    // Output:
    // [10]
    ```

## 3. Conclusion

- 6가지 JavaScript에서 사용되는 반복문에 대해서 알아보았다.
- 각 반복문에 대해서 충분한 학습을 통하여 개발코드 작성에 적절한 구문을 사용할 수 있길 바란다. (용도에 맞는 연장을 사용하길..)
- 사소한 코드 한줄 한줄이 시스템 전체에 치명적인 영향을 미칠 수 있다는 생각을 항상 하길 바랍다.
- 강조하지만, `for...in`(객체) 과 `for...of`(배열)의 차이점에 대해서 분명하게 확인하고 넘어가도록 하자.
- `for`(가장 일반적인 반복문), `for...in`(객체 타입 반복), `for...of`(배열 타입 반복), `forEach`(배열 타입의 함수), `while`(1회도 반복하지 않을 수 있음), `do...while`(최소 1회는 반복 됨)

## 4. Reference

- [MDN Site - for](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for)
- [MDN for...in](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...in)
- [MDN for...of](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...of)
- [MDN while](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/while)
- [MDN do...while](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/do...while)
- [MDN forEach](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)