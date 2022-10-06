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
last_modified_at: 2022-10-05
---

<!-- <img src="../../assets/images/posts/bootcamp005/개발자의품격001.png" width="100%"/> -->

## 1. HTML

- HTML 이란 ?([click](https://namu.wiki/w/HTML))
- `웹 사이트`의 모습을 기술하기 위한 `마크업 언어`.
- 참고 사이트
  - [W3](https://www.w3.org/)
  - [MDN](https://developer.mozilla.org/ko/)
  - [모질라재단](https://namu.wiki/w/%EB%AA%A8%EC%A7%88%EB%9D%BC%20%EC%9E%AC%EB%8B%A8)

### 1.1 Global Attributes

- 공통적으로 가지고 있는 요소들의 속성(글로벌, 전역)과 그렇지 않은 속성(로컬, 지역)
- [참고 자료](https://developer.mozilla.org/ko/docs/Web/HTML/Global_attributes)

### 1.2 Style

- 요소의 디자인을 위한 속성
- inline style
  - html 요소에 직접 스타일을 작성
- internal style
  - ```<style></style>``` tag를 활용
- external style
  - 별도의 파일(확장자 .css)에 스타일 작성 후 참조하여 사용

### 1.3 Meaningful

- `semantic tag`라는 용어로 널리사용되며, 대표적으로 시각장애의 사용자들을 위하여(스크린리더) 속성보다는 의미 있는 요소를 사용하여 접근성, 시인성을 높여준다. 
- [의미있는 요소의 대표적인 종류](https://developer.mozilla.org/ko/docs/Glossary/Semantics)
  - div, span 요소는 의미 없으며, 다른 요소를 포함(레이아웃 및 디자인)하기 위한 컨테이너 역할

### 1.4 List Tag

- 목록 표시를 위한 요소
- ul(unordered list)
  - li(list)
- ol(ordered list)
  - li(list)
- dl(description list)
  - dt(define term)
    - dd(describe description)

### 1.5 Table Tag

- 표를 표현하기 위한 속성으로, 표, 행, 셀(데이터, 열제목), 제목, 데이터들의 요소가 있다.

|     tag      | description                                       |
| :----------: | :------------------------------------------------ |
|  `<table>`   | 테이블 태그                                       |
|  `<thead>`   | 제목이 들어가는 요소로 모든 tr tag 포함           |
|  `<tbody>`   | 데이터(컨텐츠)가 들어가는 요소로 모든 tr tag 포함 |
|    `<tr>`    | 행(table row)를 위한 요소                         |
|    `<th>`    | 열제목(table head)를 위한 요소                    |
|    `<td>`    | 데이터(table data)를 위한 요소                    |
| colspan=숫자 | 열 병합                                           |
| rowspan=숫자 | 행 병합                                           |

### 1.6 Form Tag

- [`<form>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/form)
- 사용자로부터 정보를 **입력**받기 위한 *HTML 요소들*
- form tag는 client 정보를 server로 전송하기 위함이며 form action과 button submit을 이용하여 전송 가능.
- SPA(Single Page Application) 트렌드에서는 적합하지 않으며, 화면의 깜빡임 없이 서버로 정보를 전송하는 라이브러리 사용.
- `name` 속성은 그룹을 위함이며, 중복될 수 있다.
- `id` 속성은 unique한 값을 위함으로 유일해야 한다.
- `label:for` 속성에 `id`를 연결해 줌으로 그룹핑 가능.
- `<input>` 입력 요소
  - 사용자로부터 데이터를 입력 받을 수 있는 요소, HTML 제일 강력하고 복잡한 요소.
  - [input type by MDN](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)
  - 모바일 환경을 고려하여 적극적으로 사용 권장
- `<img>` 태그에는 반드시 **alt** 속성을 부여 한다.
  
### 1.7 Input Attribute

- [MDN `<input>` Link](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)
- `Form`, `Button(Submit)` 사용시 `Required` 속성에 대해서는 유효성 검사를 수행
- disabled 속성
  - submit 버튼을 통하여 서버로 전송시 value의 데이터가 전송되지 않음. [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input#attr-disabled)

```html
<form action="">
  <!-- value 값을 서버로 전송 -->
  <input type="text" name="" id="Send" value="this is id"/>

  <!-- disabled 속성 값 때문에, value 값을 서버로 전송하지 않음 -->
  <input type="text" name="" id="noSend" value="this is id" disabled/>
  <button type="submit">send to server</button>
</form>
```

- maxlength
  - password, search, tel, text, url에서 **value의 최대 길이 (문자수)** [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input#attr-maxlength)
- placeholder
  - password, search, tel, text, url에서 **양식 컨트롤이 비어있는 때 양식 컨트롤에 나타나는 내용** [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input#attr-placeholder)
- autocomplete 속성
  - name 속성과 함께 사용 가능 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Attributes/autocomplete)
- autofocus
  - 화면이 나타날때 자동으로 포커스 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input#attr-autofocus)

### 1.8 Etc Element

- `<select>` 요소 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/select)
  - 하위 데이터 요소로 `<option>` 사용 가능
    - `value` 속성 : 데이터를 식별할 수 있는 유일한 키 값

```html
<select name="" id="">
  <option value="001">data 1</option>
  <option value="002">data 2</option>
  <option value="003">data 3</option>
</select>
```

- `<select>`와, `<input type='check'/>`와 `<input type='radio'/>`를 UI와 비지니스를 고려하여 사용 필요
- `<textarea>`
  - 멀티라인 일반 텍스트 편집 컨트롤 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/textarea)
- `<fieldset>`, `<legend>` 요소
  - 여러 컨트롤과 레이블을 묶을 때 사용 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/fieldset)
- `<datalist>` 요소
  - 다른 컨트롤에서 고를 수 있는(가능한, 추천하는) 선택지를 나타내는 `<option>` 요소를 여럿 가짐 [MDN 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/datalist)
  - 동일한 화면(UI, Page)의 여러곳에서 동일한 데이터를 사용하는 경우 유용함

## 2. Environment Configure

- 개발 환경 설정
  - Visual Studio Code, Nodejs 필수

### 2.1 [VS code](https://code.visualstudio.com/)

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

### 2.2 [Nodejs](https://nodejs.org/en/)
