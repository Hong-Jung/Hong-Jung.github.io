---
title:  "[BootCamp 5기] - HTML"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, html]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-04
last_modified_at: 2022-10-04
---

<!-- <img src="../../assets/images/posts/bootcamp005/개발자의품격001.png" width="100%"/> -->

## 1. HTML

- HTML 이란 ?([click](https://namu.wiki/w/HTML))
- `웹 사이트`의 모습을 기술하기 위한 `마크업 언어`.
- 참고 사이트
  - [W3](https://www.w3.org/)
  - [MDN](https://developer.mozilla.org/ko/)
  - [모질라재단](https://namu.wiki/w/%EB%AA%A8%EC%A7%88%EB%9D%BC%20%EC%9E%AC%EB%8B%A8)

### 1.1 HTML 주요 사항

#### 1.1.1 Global Attributes

- 공통적으로 가지고 있는 요소들의 속성(글로벌, 전역)과 그렇지 않은 속성(로컬, 지역)
- [참고 자료](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes)

### 1.1.2 Style

- 요소의 디자인을 위한 속성
- inline style
  - html 요소에 직접 스타일을 작성
- internal style
  - <style></style> tag를 활용
- external style
  - 별도의 파일(확장자 .css)에 스타일 작성 후 참조하여 사용

### 1.1.3 Meaningful

- `semantic tag`라는 용어로 널리사용되며, 대표적으로 시각장애의 사용자들을 위하여(스크린리더) 속성보다는 의미 있는 요소를 사용하여 접근성, 시인성을 높여준다. 
- [의미있는 요소의 대표적인 종류](https://developer.mozilla.org/ko/docs/Glossary/Semantics)
  - div, span 요소는 의미 없으며, 다른 요소를 포함(레이아웃 및 디자인)하기 위한 컨테이너 역할

### 1.1.4 List Tag

- 목록 표시를 위한 요소
- ul(unordered list)
  - li(list)
- ol(ordered list)
  - li(list)
- dl(description list)
  - dt(define term)
    - dd(describe description)

### 1.1.5 Table Tag

- 표를 표현하기 위한 속성으로, 표, 행, 셀(데이터, 열제목), 제목, 데이터들의 요소가 있다.
- table
  - thead
    - 제목이 들어가는 요소로 모든 tr tag 포함
- tbody
  - 데이터(컨텐츠)가 들어가는 요소로 모든 tr tag 포함
- tr
  - 행(table row)를 위한 요소
- th
  - 열제목(table head)를 위한 요소
- td
  - 데이터(table data)를 위한 요소
- colspan, rowspan

### 1.1.6 Form Tag

- 하위 항목
  
### 1.1.7 Input Attribute

- 하위 항목

## 2. Environment Configure

- [VS code](https://code.visualstudio.com/)
  - Extension
    - HTML CSS support
    - HTML Snippets
    - JavaScript(ES6) code Snippets
    - ESLint
    - Prettier - Code formatter
      - settings > formatter > default formatter > prettier - code formatter
      - settings > formatter > HTML > format:Enable
      - settings > formatter > JavaScript > format:Enable
    - Live Server
- [Nodejs](https://nodejs.org/en/)
