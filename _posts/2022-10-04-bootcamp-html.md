---
title:  "HTML"
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
last_modified_at: 2022-10-07
---

<!-- <img src="../../assets/images/posts/bootcamp005/개발자의품격001.png" width="100%"/> -->

## 1. HTML

- HTML 이란 ?([click](https://namu.wiki/w/HTML))
- `웹 사이트`의 모습을 기술하기 위한 `마크업 언어`.
- 참고 사이트
  - [W3](https://www.w3.org/)
  - [MDN](https://developer.mozilla.org/ko/)
  - [모질라재단](https://namu.wiki/w/%EB%AA%A8%EC%A7%88%EB%9D%BC%20%EC%9E%AC%EB%8B%A8)

<img src="https://velog.velcdn.com/images%2Fhadoyaji%2Fpost%2F441a79f9-24d3-44c2-abfc-73d7dfbaa8f0%2Fimage.png" with="70%" alt="DOM, BOM & JavaScript"/>

- Window [MDN 참고](https://developer.mozilla.org/ko/docs/Web/API/Window)
  - Window 인터페이스는 DOM 문서를 담은 창을 나타냄
  - 최상위 객체 / 전역 객체 / 모든 객체가 소속된 객체
- DOM(Document Object Model) [MDN 참고](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)
  - 문서의 프로그래밍 interface
  - 문서의 구조화된 표현(structured representation)을 제공
  - 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법을 제공하여 그들이 문서 구조, 스타일, 내용 등을 변경할 수 있게 함
  - 브라우저가 웹 문서를 이해할 수 있도록 구성된 것
  - 자바스크립트를 통해 동적으로 변경 가능
- BOM(Browser Object Model) [Wiki 참고](https://en.wikipedia.org/wiki/Browser_Object_Model)
  - 브라우저 객체 모델 : 자바스크립트가 브라우저와 소통하기 위해 만들어진 모델
- JavaScript [MDN 참고](https://developer.mozilla.org/ko/docs/Web/JavaScript)
  - 가벼운 객체 지향 인터프리터 언어이며 웹페이지의 스크립트 언어로 잘 알려져 있지만, 브라우저가 아닌 환경에서도 많이 사용

---

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

### 1.9 Form Element

- form 요소

```html
<form action="" method="" target="" novalidate>
  <button type="submit" formnovalidate="formnovalidate">저장</button>
</form>
```

- action 속성
  - 데이터를 전송할 서버의 주소
- method 속성
  - 데이터의 전송 방법
  - get
  - url에 전송할 데이터가 포함되어 전송, 데이터 노출, 보안취약, 데이터 크기 제약
  - 페이지 주소를 공유 할때 유용(퍼머링크)
  - post
  - 전송할 데이터가 보이지 않음, get 방식보다는 보안상 안전(볼수 있음)
  - 전송할 데이터 암호화가 필요(https 프로토콜 사용하면 네트워크에서 모니터링 불가)
  - 데이터의 크기에 제약이 없음
- target 속성
  - _self(자기자신, 기본값),_blank(새창), _parent(iframe에서 바로 위의 부모),_top(iframe에서 최상위 부모)
- form 요소내 input 요소의 validate 미적용
  - form > novalidate 속성 사용
  - button > formnovalidate="formnovalidate" 속성 사용

### 1.10 iframe Element

- [W3 School 참고](https://www.w3schools.com/tags/tag_iframe.asp)
- html 페이지에 다른 html 페이지를 삽입하여 사용할 수 있음
- 요즘의 웹프레임워크(리액트, 앵귤러, 뷰)에서는 사용하지 않으며, 대형 포털에서는 iframe을 지원하지 않음

### 1.11 Video & Audio Element

- video element
  - [W3 School 참고](https://www.w3schools.com/html/html5_video.asp)
  - controls
    - 비디오 관련된 컨트롤 UI 제공
  - autoplay
    - 자동 실행
  - muted
    - 소리 제거
  - loop
    - 영상 자동 재생
  - poster
    - 썸네일
  - preload : auto, metadata, none
    - auto
      - 미리 다운로드, 시청할 확율이 높고, 영상 플레이 했을 때 바로 보여줘야 하는 중요한 영상
    - metadata
      - 미리 다운로드 안함, 메타 정보만 미리 다운로드
    - none
      - 미리 다운로드 암함, 영상을 바로 보지 않을 확율이 높음, 서버 부담 작음
- audio element
  - [W3 School 참고](https://www.w3schools.com/html/html5_audio.asp)
  - autoplay
    - 자동 다운로드후 가장 빠른 시점부터 자동 재생
  - loop
    - 자동 재생
  - muted
    - 소리 제거
  - preload
    - auto, metadata, none

### 1.12 map Element

- [W3 School 참고](https://www.w3schools.com/tags/tag_map.asp)
- [www.image-map.net 이미지 map 자동 요소 및 속성 생성 사이트](https://www.image-map.net/)
- `<map>` 태그는 이미지 맵 정의에 사용, 이미지 맵은 클릭 가능한 영역이 있는 이미지를 의미
- `<map>` 요소의 필수 이름 속성은 `<img>`의 **usemap** 속성과 연결되어 이미지와 지도 간의 관계를 생성
- `<map>` 요소에는 이미지 맵에서 클릭 가능한 영역을 정의하는 다수의 `<area>` 요소가 포함
  
```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap" width="400" height="379">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
  <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
  <area shape="circle" coords="337,300,44" alt="Cup of coffee" href="coffee.htm">
</map>
```

### 1.13 Semantic Element

- [W3 School 참고](https://www.w3schools.com/html/html5_semantic_elements.asp)
- 많은 웹 사이트에는 `탐색`, `머리글` 및 `바닥글`을 나타내는 `<div id="nav"> <div class="header"> <div id="footer">` 와 같은 HTML 코드가 포함되어 있음
  - 의미 없이 `div` 요소가 중첩하여 수없이 사용되면, 유지보수 및 가독성 모든 면에서 나쁜 영향을 끼침
- 태그(요소)를 개발자들만 인지할 수 있도록 작성되는 부분을 지양하고, 의미 있는 태그(요소)를 적극적으로 사용하여 가독성, 접근성을 높일 수 있도록 `Semantic Tag` 사용을 지향
- 시멘틱 요소는 100% `<div>` 요소와 동일하다.

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
