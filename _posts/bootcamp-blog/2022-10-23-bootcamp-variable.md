---
title:  "JavaScript in Variable Declaration."
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
 
date: 2022-10-24
last_modified_at: 2022-10-24
---

# What is ***variable(변수) declaration(선언)*** in JavaScript ???

## 0. Index

- [What is ***variable(변수) declaration(선언)*** in JavaScript ???](#what-is-variable변수-declaration선언-in-javascript-)
  - [0. Index](#0-index)
  - [1. Introduction](#1-introduction)
    - [1.1 변수란 ?](#11-변수란-)
    - [1.2 변수의 명명 이란?](#12-변수의-명명-이란)
    - [1.3 변수의 선언 이란?](#13-변수의-선언-이란)
  - [2. Body](#2-body)
    - [2.1 변수의 명명 규칙](#21-변수의-명명-규칙)
      - [2.1.1 카멜표기법(camelCase)](#211-카멜표기법camelcase)
      - [2.1.2 스네이크 표기법(snake_case)](#212-스네이크-표기법snake_case)
      - [2.1.3 파스칼 표기법(PascalCase)](#213-파스칼-표기법pascalcase)
      - [2.1.4 헝가리언 표기법(데이터타입의 약어사용)](#214-헝가리언-표기법데이터타입의-약어사용)
    - [2.2 변수 선언자](#22-변수-선언자)
      - [2.2.1 var](#221-var)
      - [2.2.2 let](#222-let)
      - [2.2.3 const](#223-const)
  - [3. Conclusion](#3-conclusion)
  - [4. Reference](#4-reference)

## 1. Introduction 

- 블로그에서 다루는 내용
  - 프로그래밍을 함에 있어 목적 달성을 위하여 여러가지 방법으로 코드를 만들 수 있다. 코드를 만듬에 있어 가장 중요하고 기초적인 부분이 변수의 이름을 지어주고, 변수의 타입을 지정해 주는것이 이다.
  - `변수란 변할 수 있는 수(값, 데이터)`이라고 아주 간단하게 정의할 수 있겠다. 그럼 변할 수 있는 수(값, 데이터)를 어떻게 이름을 지어주어야하며, 어떤 타입으로 선언하여 사용할 수 있는지에 대해서 알아보자.
  - 변수의 이름을 지어주는 부분이 `변수의 명명`이라고 하며, 어떻게 이름을 지어주는지에 따라 공동작업(협업, 개인 작업도 동일)에 있어 무엇보다도 중요하다. 시스템의 론칭이후, 유지/보수때 코드 가독성에 긍정적인 영향을 미치는 1순위라고 해도 과언이 아니다. 이를 위하여 프로젝트 전 명명 규칙에 대한 가이드 라인을 작성하고 지속적으로 변경하며 공동작업에 참고한다.
  - 변수의 이름을 잘 지어 주었다면, 다음은 변수를 어떤 용도로 사용할지에 따라 선언자를 구분해 주어야 한다. 공통 작업(협업)에 있어 선언자를 적절하게 구분하여 사용함으로 코드의 오류를 사전에 방지할 수 있다.

### 1.1 변수란 ?

- 변수에 대한 정의
  - 영어로 `Variable`이며, 코드가 실행될 때 변경될 수 있는 값이며, 변경될 수 있는 값에 이름이 부착되어 이름으로 접근이 가능하다.
  - 데이터(값)에 대해서 보관할 수 있는 영역(메모리)이며, 크기와 타입에 조금씩 다르다.
- 변수의 이름을 지어주는 일반적인 방법에 대해서 알아본다.
- 변수의 사용을 위해서 이름을 지어주고 사용을 알려주는 방법에 대해서 알아본다.
- 각 변수 선언의 타입의 특성에 대해서 알아본다.

### 1.2 변수의 명명 이란?

- 변수를 사용하기 위해서는 이름을 지어주어야 한다. 이를 `변수의 명명 규칙`이라고 하며, 4가지의 가장 대표적인 명명 규칙에 대해서 알아보자.  

### 1.3 변수의 선언 이란?

- 변수의 선언
  - 변수의 사용을 사전에 알린다고 생가가면 쉽다. 엄격하게 모든 변수는 사용전에 선언이라는 코드를 사용하여 반드시 사용하겠다고 알려야 한다.

## 2. Body

### 2.1 변수의 명명 규칙

- `ES6에서도 카멜표기법을 따라서 사용하며, 일반적으로 가장 많이 사용`

#### 2.1.1 카멜표기법(camelCase)

- [카멜표기법(camelCase)](https://ko.wikipedia.org/wiki/%EC%B9%B4%EB%A9%9C_%ED%91%9C%EA%B8%B0%EB%B2%95)
- `낙타 표기법`으로 첫글자는 소문자, 다음 문자부터는 첫글자 대문사로 사용
  
  - ```javascript 
    var userName = "walter";
    ```

#### 2.1.2 스네이크 표기법(snake_case)

- [스네이크 표기법(snake_case)](https://ko.wikipedia.org/wiki/%EC%8A%A4%EB%84%A4%EC%9D%B4%ED%81%AC_%ED%91%9C%EA%B8%B0%EB%B2%95)
- `스네이크 표기법`으로 `스테이크(_)` 문자를 단어와 단어사이에 사용
  
  - ```javascript 
    var user_name = "walter";
    ```

#### 2.1.3 파스칼 표기법(PascalCase)

- 파스칼 표기법(PascalCase)
- `쌍봉낙타 표기법`으로 각 단어의 조합에서 단어의 첫글자를 대문자로 사용
  
  - ```javascript 
    var UserName = "walter";
    ```

#### 2.1.4 헝가리언 표기법(데이터타입의 약어사용)

- [헝가리언 표기법(데이터타입의 약어사용)](https://ko.wikipedia.org/wiki/%ED%97%9D%EA%B0%80%EB%A6%AC%EC%95%88_%ED%91%9C%EA%B8%B0%EB%B2%95)
- `헝가리언 표기법`으로 `자료형(데이터 타입)`의 약어를 변수명의 앞에 사용
- 자료형이 바뀐다면?? 전체 변수명을 찾아 수정해 주어야 한다.

  - ```javascript 
    var strUserName = "walter"; // string의 약어인 str 사용
    ```

### 2.2 변수 선언자

- 변수 선언자 란?
  - 변수 선언에 사용하는 3가지 키워드로 `var, let, const`가 있다.
  
#### 2.2.1 var

- 선언한 변수명에 데이터를 다시 할당할 수 있음
- 동일한 변수명으로 재 선언 할 수 있음
- 문제점 ?
  - 이미 선언한 변수에 값도 다시 할 당 할 수 있고(여긴 그나마 문제가 덜됨), 하지만 동일한 변수명을 다시 재 선언함으로 코드의 오류가 발생(공동 작업이나, 원 변수의 의미를 알지 못한다면). 그래서 `ES6`에서 `let`, `const`라는 변수 선언자가 생겼다.
- 샘플 코드
  - <iframe height="300" style="width: 100%;" scrolling="no" title="var variable" src="https://codepen.io/jh3010/embed/ExRVyeg?default-tab=js%2Cresult&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true"/>

#### 2.2.2 let

- 선언한 변수명에 데이터를 다시 할달할 수 있음
- 동일한 변수명으로 재 선언 할 수 없음
- 샘플 코드
  - <iframe height="300" style="width: 100%;" scrolling="no" title="let variable" src="https://codepen.io/jh3010/embed/vYrNKVR?default-tab=js%2Cresult&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/jh3010/pen/vYrNKVR">
  let variable</a> by walter (<a href="https://codepen.io/jh3010">@jh3010</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

#### 2.2.3 const

- 변수를 선언하는 시점에 값을 반드시 할당해야 함
- 동일한 변수명을 재 선언 할 수 없으며, 값을 재 할당 할 수도 없음
- 샘플 코드
  - <iframe height="300" style="width: 100%;" scrolling="no" title="const variable" src="https://codepen.io/jh3010/embed/eYKpzQJ?default-tab=js%2Cresult&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/jh3010/pen/eYKpzQJ">
  const variable</a> by walter (<a href="https://codepen.io/jh3010">@jh3010</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

## 3. Conclusion

- 결언

## 4. Reference

- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)