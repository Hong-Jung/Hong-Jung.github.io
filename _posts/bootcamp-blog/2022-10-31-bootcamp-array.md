---
title:  "[Blog] JavaScript in Arrary."
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, Arrary]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-11-06
last_modified_at: 2022-11-06
---

# What is ***Arrary(배열)*** in JavaScript ?

## 0. Index

- [What is ***Arrary(배열)*** in JavaScript ?](#what-is-arrary배열-in-javascript-)
  - [0. Index](#0-index)
  - [1. Introduction](#1-introduction)
    - [1.1 배열(Arrary) 객체란 ?](#11-배열arrary-객체란-)
    - [1.2 배열은 왜 필요할까 ?](#12-배열은-왜-필요할까-)
    - [1.3 배열 객체의 내장 함수 종류는 ?](#13-배열-객체의-내장-함수-종류는-)
  - [2. Body](#2-body)
    - [2.1 toString()](#21-tostring)
    - [2.2 join()](#22-join)
    - [2.3 push()](#23-push)
    - [2.4 unshift()](#24-unshift)
    - [2.5 pop()](#25-pop)
    - [2.6 shift()](#26-shift)
    - [2.7 splice()](#27-splice)
    - [2.8 concat()](#28-concat)
    - [2.9 slice()](#29-slice)
    - [2.10 sort()](#210-sort)
    - [2.11 filter()](#211-filter)
    - [2.12 map()](#212-map)
    - [2.13 reduce()](#213-reduce)
  - [3. Conclusion](#3-conclusion)
    - [3.1 어디서 사용할 것인가 ? (활용도)](#31-어디서-사용할-것인가--활용도)
    - [3.2 최종 정리](#32-최종-정리)
  - [4. Reference](#4-reference)

## 1. Introduction 

- 블로그에서 다루는 내용
  - 자바스크립트에서는 기본 데이터 타입이 몇가지 있습니다. 그중 반드시 알아야하며, 가장 많이 사용하는 기본 데이터 타입 객체가 다음과 같습ㄴ다.
    - 문자열, 숫자형, 참/거짓, undefined, null, object, arrary
  - 몇가지 기본 데이터 타입중에서 이번 블로그에서는 array object에 대해서 중점적으로 알아 보겠습니다.
  - Arrary Object가 무엇인지, 왜 필요해서 우리가 알아야 하는지, 상세한 내장 함수(객체 하위의 function 또는 property)는 어떠한 것들이 존재하는지 마지막으로 그래서 어디서 활용하는지 알아보겠습니다.

### 1.1 배열(Arrary) 객체란 ?

- [MDN Site에서의 Array 객체의 설정/정의](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)
  - `리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체`
    - 리스트형태 즉, 목록의 형태를 띠는 객체이다. 즉, 무엇인지 모르지만 개발자가 작성하게 될 값이 목록의 형태를 가지고 있습니다.
  - `배열의 요소 인덱스로 문자열을 사용할 수 없으며 무조건 정수만 허용` 
    - 배열의 목록에 접근하기 위해서는 정수(인덱스, 번호)로만 지정하여 사용가능 합니다.

```javascript
// 0.1 배열 만들기
let fruits = ['사과', '바나나']

console.log(fruits.length)
// 2

// 0.2 인덱스로 배열의 항목에 접근하기
let first = fruits[0]
// 사과

let last = fruits[fruits.length - 1]
// 바나나

// 0.3 배열의 항목들을 반복하며 처리하기
fruits.forEach(function (item, index, array) {
  console.log(item, index)
})
// 사과 0
// 바나나 1
```

### 1.2 배열은 왜 필요할까 ?

- 배열(Array)은 서로 관련이 있는 데이터끼리의 모음으로 하나의 모음으로 관리하기 위한 데이터 타입의 한 종류 이며, 객체 입니다.
  - 실제 코딩의 경우를 생각해 봅시다. (Case Study)
    - 처리할 데이터의 종류가 5개가 존재 한다고 가정하며, 각 데이터는 다음과 같습니다.
    - first name, last name, age, email, phone
    - 배열 없이 일반 변수로 5개의 데이터를 정의하고 할당하며, 출력 합니다.

    - ```javascript
      let firstName = "John";
      let lastName = "Doe";
      let age = 23;
      let email = "john.doe@email.com";
      let phone = "111-2222-3333";

      console.log(firstName);//output: 
      console.log(lastName);//output: 
      console.log(age);//output: 
      console.log(email);//output: 
      console.log(phone);//output: 
      ```

    - 쉽죠? 5개 변수를 선언하고 각 선언한 변수에 데이터베이스로부터 수신한 값? 또는 로직으로 사용할 값을 할당 합니다. 각 할당한 값을 하나씩 출력해 봅니다.
    - 자, 여기서 다음의 요구사항? 요건에 대해서 어떤 해결책이 있을까요?
      - 5개의 변수의 값을 하나의 문자열로 합치고 싶다면?
      - 주소라는 속성이 추가되어 더하고 싶다면?
      - firstName, lastName 기준으로 오름차순 혹은 내림차순으로 정렬하고 싶다면?
    - 해결책은 너무도 다양 합니다. 이러한 요구사항의 해결책을 어떠한 것이 최선일까?라는 문제로 접근할 것이 아니라, 이미 이러한 요구사항의 해결책을 위하여 만들어 놓은 것이 Array 객체가 그중 하나 입니다.
  
    - ```javascript
      let person = ["John", "Doe", 23, "john.doe@email.com", "111-2222-3333"];
      console.log(person);
      //output: Array(5) [ "John", "Doe", 23, "john.doe@email.com", "111-2223-3333" ]
      ```

    - 3가지 요구사항뿐 아니라, 더 많은 요구의 해결을 위한 Array 객체의 하위에 함수나 속성 형태로 이미 제공되고 있습니다. 우리는 이미 만들어진 함수나 속성에 대해서 정확한 쓰임새를 익힘으로 무한의 활용이 가능해 집니다.
      - 1차원 배열의 경우는 위의 샘플 코드와 같이 하나의 연관 데이터(John Doe)만 정의하지만, 2차원 배열의 경우 연관된 데이터의 묶음을 무수하게 정의하고, 정의된 배열 객체의 데이터를 손쉽게 다룰 수 있습니다.

### 1.3 배열 객체의 내장 함수 종류는 ?

|                                                 함수 이름                                                  | 간략 설명                                                             |
| :--------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------- |
| [toString()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) | 문자열 객체로 변환하여 반환                                           |
|     [join()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)     | 파라미터의 문자가 요소 사이 삽입되어 하나의 문자로 반환               |
|     [push()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push)     | 파라미터의 문자를 마지막 요소로 추가                                  |
|  [unshift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)  | 파라미터의 문자를 첫번째 요소로 추가                                  |
|      [pop()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)      | 마지막 요소 제거 후 반환                                              |
|    [shift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)    | 첫번째 요소 제거 후 반환                                              |
|   [splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)   | 특정 위치에 요소 추가, 추가시 삭제도 가능                             |
|   [concat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)   | 2개 이상의 배열 결합                                                  |
|    [slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)    | 요소를 잘라내서 배열 타입으로 반환                                    |
|     [sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)     | 요소를 정렬                                                           |
|   [filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)   | 특정 조건의 요소를 찾고 배열로 반환                                   |
|      [map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)      | 배열의 요소가 객체의 경우(key-value), 새로운 객체로 변경 후 배열 반환 |
|   [reduce()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)   | 요소의 크기만큼 callback 호출(재귀 호출)하면서 누적된 값을 출력       |

## 2. Body

### 2.1 toString()

- 문자열 객체로 변환하여 반환
  
> toString()
>> `toString()` 메서드는 지정된 배열 및 그 요소를 나타내는 문자열을 반환합니다.
>>>
>>> ```javascript
>>> let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
>>> console.log(brands.toString());
>>> // Output:
>>> // 애플,구글,아마존,마이크로소프트,메타
>>> ```

- code sample

```javascript
// this is code sample
```

### 2.2 join()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.3 push()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.4 unshift()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.5 pop()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.6 shift()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.7 splice()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.8 concat()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.9 slice()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.10 sort()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.11 filter()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.12 map()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

### 2.13 reduce()

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

- code sample

```javascript
// this is code sample
```

## 3. Conclusion

### 3.1 어디서 사용할 것인가 ? (활용도)

- content

### 3.2 최종 정리

- 6가지 JavaScript에서 사용되는 반복문에 대해서 알아보았다.
- 각 반복문에 대해서 충분한 학습을 통하여 개발코드 작성에 적절한 구문을 사용할 수 있길 바란다. (용도에 맞는 연장을 사용하길..)
- 사소한 코드 한줄 한줄이 시스템 전체에 치명적인 영향을 미칠 수 있다는 생각을 항상 하길 바랍다.
- 강조하지만, `for...in`(객체) 과 `for...of`(배열)의 차이점에 대해서 분명하게 확인하고 넘어가도록 하자.
- `for`(가장 일반적인 반복문), `for...in`(객체 타입 반복), `for...of`(배열 타입 반복), `forEach`(배열 타입의 함수), `while`(1회도 반복하지 않을 수 있음), `do...while`(최소 1회는 반복 됨)

## 4. Reference

- [MDN Site - Arrary](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)