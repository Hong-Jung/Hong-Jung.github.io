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
  - 자바스크립트에서는 기본 데이터 타입이 몇가지 있습니다. 그중 반드시 알아야하며, 가장 많이 사용하는 기본 데이터 타입은 다음과 같습ㄴ다.
    - 문자열, 숫자형, 참/거짓, undefined, null, object, arrary
  - 몇가지 기본 데이터 타입중에서 이번 블로그에서는 array object에 대해서 중점적으로 알아 보겠습니다.
  - Arrary Object가 무엇인지, 왜 필요해서 우리가 알아야 하는지, 상세한 내장 함수는 어떠한 것들이 존재하는지 마지막으로 그래서 어디서 많이 활용하는지 알아보겠습니다.

### 1.1 배열(Arrary) 객체란 ?

- JavaScript에서 `조건`에 따라 `반복`되는 작업을 수행하는 데 사용되며, 조건은 일반적으로 `true` 또는 `false를` 반환한다. `반복은 정의된 조건이 false를 반환할 때까지 계속 실행` 된다.

### 1.2 배열은 왜 필요할까 ?

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

- 간략 설명
  
> 내장 객체 함수()
>> 설명
>>> text

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