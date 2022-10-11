---
title:  "CSS"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, css]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-11
last_modified_at: 2022-10-11
---

<!-- <img src="../../assets/images/posts/bootcamp005/개발자의품격001.png" width="100%"/> -->

## 1. CSS

- [CSS(Cascading Style Sheets)](https://ko.wikipedia.org/wiki/CSS)
- CSS는 웹 페이지에 스타일(디자인, 레이아웃등)을 적용할 수 있는 기술이다.
  - HTML은 웹 페이지의 뼈대를 구성하는 기술이다.
- W3C의 표준화 제정
  - [can i use ?](https://caniuse.com)
  - W3C(World Wide Web)에서 추가되는 신규 기술 사양에 대해서 표준화 제정 단계 4단계로 사용자에게 기술 사양의 상태를 알려줌
    - WD(Working Draft), CR(Candidate Recommendation), PR(Proposed Recommendation), REC(W3C Recommendation)
    - `caniuse.com`에서 CSS의 기술 사양에 대해서 상태를 상세하게 확인 가능
    - 초록색은 지원, 붉은색은 미지원

### 1.1 선택자(Selector)

- 특정 요소 및 원하는 요소에 대해서 한번에(쉽게, 편리하게) 디자인(CSS Style)을 적용할 수 있는 방법을 제공해 준다
- <img src="https://www.w3schools.com/css/img_selector.gif" width="100%"/>
- `h1` : 선택자
- `{color:blue; font-size:12px;}` : 선언 블럭(declaration block)
- `color:blue;` : 선언(declaration)
- `color` : 속성(property)
- `blue` : 속성값(property-value)
- 선택자의 종류
  - 클래스 선택자(class selector)
    - element의 class 속성값을 활용

    - ```html
      <style>
        .bg-red { background-color: red; }
      </style>
      <div class="bg-red h-100">클래스 선택자</div>
      ```

  - 태그 선택자(tag selector)
    - element 명을 활용 

    - ```html
      <style>
        a { text-decoration: none; } 
      </style>
      ```

  - ID 선택자(ID selector)
    - html 요소의 id(유일한 값)를 활용

    - ```html

      <style>
        #container { width: 1200px; margin: 20px auto; }
      </style>
      <div id="container">아이디사용</div>
      ```

  - 복합 선택자(combination selector)
    - 2개 이상의 요소에 대해서 활용 

    - ```html
      <style>
        <!-- section 요소하위 모든 ul 요소 -->
        section ul { border: 1px dotted black; } 

        <!-- section 하위 ul 요소 -->
        section>ul { border: 1px; }

        <!-- 인접한 형제 선택자 -->
        h1+ul { background: blue; }

        <!-- 일반 형제 선택자 -->
        h1~ul { background: green; }
      </style>
      ```

  - 속성 선택자(attribute selector)
    - 요소의 속성별로 활용

    - ```html
      <style>
        <!-- E[attr] -->
        a[href] { color: black; text-decoration: none; }

        <!-- E[attr="value"] -->
        input[type="text"] { width: 200px; border: 1px solid #ddd; }

        <!-- name 속성 선택자 -->
        [name='email'] { border: 2px solid blue; }
      </style>
      <input type='email' name='email' id=''/>
      ```

  - 가상 클래스 선택자(pseudo selector)
    - 특정 요소에 사용자의 이벤트(마우스 포커스, 마우스 호버등)에 대해서 스타일을 지정
    - a 요소의 text-decoration: none이후 마우스 호버시 링크 표시<br/>

    - ```html
      <style>
        <!-- :link, :visited, :hover, :active, :focus` ... -->
        a:hover { text-decoratin: underline; }

        <!-- 2n or even : 짝수, 2n+1 or odd : 홀수 -->
        tbody > tr:nth-child(2n) { background-color: yellow; }
      </style>
      ```

### 1.2 CSS 적용 방법

### 1.3 색상 적용 방법

### 1.4 텍스트 스타일링

### 1.5 글꼴 스타일링

### 1.6 목록 스타일링

### 1.7 링크와 커서 스타일링

### 1.8 표 스타일링

### 1.9 CSS 박스 모델과 요소의 크기

### 1.10 background 스타일링

### 1.11 border 스타일링

## 2. Reference

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)