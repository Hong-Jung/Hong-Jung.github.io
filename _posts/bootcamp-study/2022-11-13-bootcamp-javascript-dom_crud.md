---
title:  "JavaScript - DOM & Baisc CRUD"
excerpt: "개발자의품격"
comments: true
header:

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, JavaScript, DOM, CRUD]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-11-13
last_modified_at: 2022-11-13
---

# JavaScript DOM & Basic CRUD

- [JavaScript DOM & Basic CRUD](#javascript-dom--basic-crud)
  - [1. JavaScript DOM](#1-javascript-dom)
    - [1.1 DOM(Document Object Model)](#11-domdocument-object-model)
    - [1.2 DOM 요소(Element) 접근](#12-dom-요소element-접근)
    - [1.3 DOM 속성(Attribute)](#13-dom-속성attribute)
    - [1.4 DOM 이벤트](#14-dom-이벤트)
      - [1.4.1 Click Event](#141-click-event)
      - [1.4.2 Load Event](#142-load-event)
      - [1.4.3 Change Event](#143-change-event)
      - [1.4.4 Focus Event](#144-focus-event)
      - [1.4.5 Blur Event](#145-blur-event)
      - [1.4.6 Key Event](#146-key-event)
      - [1.4.7 Input Event](#147-input-event)
      - [1.4.8 Scroll Event](#148-scroll-event)
      - [1.4.9 Bubbling Event](#149-bubbling-event)
      - [1.4.10 Prevent Event](#1410-prevent-event)
    - [1.5 DOM 요소 변경](#15-dom-요소-변경)
    - [1.6 input validity](#16-input-validity)
  - [2. Basic CRUD](#2-basic-crud)
    - [2.1 List UI](#21-list-ui)
    - [2.2 Create UI](#22-create-ui)
    - [2.3 Detail UI](#23-detail-ui)
    - [2.4 Update UI](#24-update-ui)
    - [2.5 Multiple Create UI](#25-multiple-create-ui)
    - [2.6 Simple Data Grid](#26-simple-data-grid)
  - [3. Additional](#3-additional)
    - [3.1 LocalStorage & SessionStorage](#31-localstorage--sessionstorage)
    - [3.2 GeoLocation API](#32-geolocation-api)
    - [3.3 Web Speech API](#33-web-speech-api)
  - [4. 참고](#4-참고)

## 1. JavaScript DOM

### 1.1 DOM(Document Object Model)

- 사용자가 웹페이제 접근할때 브라우저는 해당 페이지에 대한 DOM을 생성하고, W3C의 표준(문서 접근의 표준을 정의)이다.
- HTML을 위한 표준 객체 모델 및 프로그래밍 인터페이스이다.
  - 자바스크립트로 HTML을 컨트롤 할 수 있다.
    - HTML요소 및 속성 추가 또는 변경
    - HTML 이벤트 반응
    - CSS 스타일 추가 또는 변경
- DOM Object Tree
  - <img src="https://www.w3schools.com/js/pic_htmltree.gif" width="100%" align="center"/>

### 1.2 DOM 요소(Element) 접근

```html
<div>
  <label for="userId">사용자 ID</label>
  <input type="text" name="" id="userId" class="form-control" />
</div>
<div>
  <label for="userPass">비밀번호</label>
  <input type="text" name="" id="userPass" class="form-control" />
</div>

<div>
  <input type="checkbox" name="chk_pl" id="chk_html" value="HTML" />
  <label for="chk_html">HTML</label>
  <input type="checkbox" name="chk_pl" id="chk_css" value="CSS" />
  <label for="chk_css">CSS</label>
  <input type="checkbox" name="chk_pl" id="chk_js" value="JS" />
  <label for="chk_js">JavaScript</label>
</div>
<button onclick="doSave();">저장</button>
<button onclick="doSave2();">저장2</button>
```

- `id` 값을 이용해서 접근([MDN Refer](https://developer.mozilla.org/ko/docs/Web/API/Document/getElementById))
  
  - ```javascript
    const userIdElement = document.getElementById("userId");
    ```

- `tag name`을 이용해서 접근([MDN Refer](https://developer.mozilla.org/ko/docs/Web/API/Document/getElementsByTagName))

  - ```javascript
    const labelElements = document.getElementsByTagName("label");
    ```

- `class name`을 이용해서 접근([MDN Refer](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName))

  - ```javascript
    const inputElements = document.getElementsByClassName("form-control");
    ```

- `name` 속성 값을 이용해서 접근([MDN Refer](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByName))

  - ```javascript
    const chks = document.getElementsByName("chk_pl");

    let checkedValue = [];
    for (const chk of chks) {
      if (chk.checked) {
        checkedValue.push(chk.value);
      }
    }
    ```

- `CSS selector`를 이용해서 접근 (가장 많이 사용)

  - ```javascript
    const checkedElements = document.querySelectorAll("[name=chk_pl]:checked");

    let checkedValue = [];
    for (const chk of checkedElements) {
      checkedValue.push(chk.value);
    }
    ```

  - [MDN querySelector](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector), [MDN querySelectorAll](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelectorAll)

  - ```javascript
    const userIdElement2 = document.querySelector("#userId");
    const labelElements2 = document.querySelectorAll("label");
    const inputElements2 = document.querySelectorAll(".form-control");
    ```

  - 가상클래스 이용

  - ```javascript
    const checkedElements = document.querySelectorAll("[name=chk_pl]:checked");
    ```

### 1.3 DOM 속성(Attribute)

- DOM 속성에 접근하여 값을 변경 가능

```html
<div>
  <label for="userName">당신의 이름은?(*)</label>
  <input type="text" name="" id="userName" onkeyup="checkRequired();" />
</div>
<label for="selLanguage">가장 좋아하는 프로그래밍 언어는?</label>
<select name="" id="selLanguage" value="">
  <option value="HTML">HTML</option>
  <option value="CSS">CSS</option>
  <option value="JS">JavaScript</option>
</select>
<button onclick="doSave();" id="btnSave" disabled>저장</button>
<button onclick="setLang();">설정</button>
```

- 저장 버튼 및 설정
  - 저장
    - `저장` 버튼의 `비활성화`
    - `이름` 값의 `validation` 체크(필수 입력 값)
    - `selLanguage의` 선택된 값을 데이터베이스에 `저장`
    - 저장 완료 후 `저장` 버튼 `활성화`
  - 설정
    - `selLanguage의` 값을 "JS"로 `변경`
  - userName validation
    - `사용자 이름`이 입력되면 `저장` 버튼을 `활성`, 아니면 `비활성`

  - ```javascript
    function doSave() {
      // 버튼 비활성화
      document.querySelector("#btnSave").disabled = true;
      if (document.querySelector("#userName").value === "") {
        return alert("이름은 필수 입력값입니다.");
      }

      const favoriteLang = document.querySelector("#selLanguage").value;
      console.log(favoriteLang);

      // 서버와 통신하고 응답을 받았다고 가정
      setTimeout(function () {
        document.querySelector("#btnSave").disabled = false;
      }, 2000);
    }
    ```

  - ```javascript
    function setLang() {
      document.querySelector("#selLanguage").value = "JS";
    }

    function checkRequired() {
      const userNameElement = document.querySelector("#userName");
      if (userNameElement.value.length > 0) {
        document.querySelector("#btnSave").disabled = false;
      } else {
        document.querySelector("#btnSave").disabled = true;
      }
    }
    ```

### 1.4 DOM 이벤트

- DOM 객체의 다양한 이벤트

#### 1.4.1 Click Event

- 마우스 좌측 버튼 클릭시 발생하는 이벤트

```html
<button onclick="myFunction();">클릭</button>
<button id="btn2">클릭2</button>
<script>
  //사용자 마우스 왼쪽 클릭
  //HTML 요소의 on + event와 같은 형식으로 이벤트 등록 가능
  function myFunction() {
    console.log("onclick 이벤트 발생");
  }

  //addEventListener(이벤트명, 콜백함수)의 형식으로 이벤트 등록 가능
  document.querySelector("#btn2").addEventListener("click", function () {
    console.log("이벤트 리스너 사용");
  });
</script>
```

#### 1.4.2 Load Event

- Javascript의 코드와 HTML DOM 객체 생성의 순서에서 발생하는 문제를 해결하기 위해서 load 이벤트를 통하여 html DOM 객체 트리가 모두 생성된 후 javascript 코드를 수행한다.
- html DOM 객체 트리 생성 > load 이벤트 정의 > 이벤트 리스너 모음 함수 호출 > 정의할 이벤트 리스너 정의
  
  - ```javascript
    // HTML tag가 DOM tree에 추가되었을 때
    window.addEventListener("load", () => { 코드블럭 }); 
    // 현재 페이지가 다른 페이지 이동 또는 닫을때
    window.addEventListener("unload", () => { 코드블럭 }); 
    ```

```html
<button id="btnSearch">조회</button>
<button id="btnDelete">삭제</button>
<script>
  function setEvent() {
    document
      .getElementById("btnSave")
      .addEventListener("click", function () {
        console.log("저장 실행");
      });

    document
      .getElementById("btnSearch")
      .addEventListener("click", function () {
        console.log("조회 실행");
      });

    document
      .getElementById("btnDelete")
      .addEventListener("click", function () {
        console.log("삭제 실행");
      });
  }

  // load - HTML 태그가 DOM 객체 트리 모델로 모두 추가가 되었을 때
  window.addEventListener("load", () => {
    setEvent();
  });

  // unload - 현재 페이지에서 다른 페이지로 이동할때, 혹은 페이지를 닫을 때
  window.addEventListener("unload", () => {
  });
</script>
```

#### 1.4.3 Change Event

- 변경(값, 속성 등)되었을때 발생하는 이벤트
  - select & option, checkbox

```html
<select name="" id="sel" onchange="doChange();">
  <option value="KO">Korea</option>
  <option value="CN">China</option>
  <option value="JP">Japan</option>
</select>
<div>
  <input
    type="checkbox"
    name=""
    id="chkAgreement"
    onchange="doChange2();"
  />
  <label for="chkAgreement">동의합니다</label>
</div>
<script>
  // change
  function doChange() {
    console.log(document.querySelector("#sel").value);
  }

  function doChange2() {
    console.log(document.querySelector("#chkAgreement").checked);
  }
</script>
```

#### 1.4.4 Focus Event

- 사용자가 키보드로 key-in하여 입력할때 발생하는 이벤트

```html
<style>
  /* 가상 클래스로 쉽게 정의 가능 */
  /* input:focus {
    border: 5px dotted green;
  } */
</style>

<input type="text" name="" id="" onfocus="myFunction()" />
<input type="text" name="" id="" onfocus="myFunction()" />
<br />
<input type="text" name="" id="" onfocus="myFunction()" />
<br />
<input type="text" name="" id="" onfocus="myFunction()" />
<script>
  // focus
  function myFunction() {
    console.log("focus 이벤트");
  }
</script>
```

#### 1.4.5 Blur Event

- focus 이벤트와 반대되는 이벤트로 포커스가 빠질때 발생하는 이벤트

```html
<input type="text" name="" id="str" onblur="myFunction()" />
<span id="strMsg" style="display: none; color: red">필수 입력 값입니다.</span>
<script>
  // blur - 포커스가 빠져나올때
  function myFunction() {
    console.log("blur 이벤트");

    if (document.getElementById("str").value === "") {
      //alert("필수 입력 값입니다.");
      document.getElementById("strMsg").style.display = "";
      document.getElementById("str").focus();
    } else {
      document.getElementById("strMsg").style.display = "none";
    }
  }
</script>
```

#### 1.4.6 Key Event

- Keyboard의 key 입력 이벤트로 다음와 같이 3가지 순서로 발생
  - keydown
  - keypress
  - keyup
    - 입력하는 키보드의 값(value)가 속성에 할당 됨
- 이벤트에서는 이벤트 발생시 해당 이벤트가 발생한 요소의 객체를 바로 사용할 수 있다.
  
- ```javascript
  console.log(event.type);
  console.log(event.target);
  console.log(event.target.value);
  console.log(event.keycode);
  console.log(event.path);
  ```

- 이벤트 취소(막기)

- ```javascript
  event.preventDefault(); 
  ```

```html
<input type="text" name="" id=""
       onkeydown="myFunction()"
       onkeypress="myFunction()"
       onkeyup="myFunction()"/>
<br />
<input type="text" name="" id="id1" onkeyup="moveNext();" />-<input type="text" name="" id="id2"/>
<br />
<input type="text" name="" id="" onkeypress="onlyNumber();" />
<script>
  // keydown -> keypress -> keyup
  function myFunction() {
    console.log(event.type);
    // console.log(event.target);
    console.log(event.target.value);//keyup 이벤트 시점에 사용자가 입력한 값이 value 속성에 들어 감
  }

  // 주민번호 앞자리 6자리 다 입력하면 자동으로 다음 컨트롤로 이동
  function moveNext() {
    if (event.target.value.length === 6) {
      document.querySelector("#id2").focus();
    }
  }

  function onlyNumber() {
    console.log(event.keyCode);
    // 0 - 48
    // 9 - 57
    if (event.keyCode >= 48 && event.keyCode <= 57) {
    } else {
      event.preventDefault(); // 이벤트 중지 시킴
    }
  }
</script>
```

#### 1.4.7 Input Event

- input event가 뒤에 추가 되었음
- keydown > keypress > keyup(기존)
- keydown > keypress > input(value 속성에 값이 할당 되는 시점에 발생-사용자 눈에 안 보임) > keyup(value 속성에 값이 할당 완료된 시점에 발생-사용자 눈에 보임) (추가)

```html
<div>
  <label for="number">숫자만 입력 가능한 필드</label>
  <input type="text" name="" id="number" oninput="onlyNumber();" />
</div>
<div>
  <label for="lowercase">소문자만 입력 가능한 필드</label>
  <input type="text" name="" id="lowercase" oninput="onlyLowercase();" />
</div>
<div>
  <label for="uppercase">대문자만 입력 가능한 필드</label>
  <input type="text" name="" id="uppercase" oninput="onlyUppercase();" />
</div>
<div>
  <label for="korean">한글만 입력 가능한 필드</label>
  <input type="text" name="" id="korean" oninput="onlyKorean();" />
</div>
<script>
  function onlyNumber() {
    const regexp = /\D/g; // 숫자가 아닌 모든 문자를 모두 찾아라
    console.log(event.target.value);
    event.target.value = event.target.value.replace(regexp, "");
  }

  function onlyLowercase() {
    const regexp = /[^a-z]/g; // 소문자가 아닌 모든 문자를 모두 찾아라
    console.log(event.target.value);
    event.target.value = event.target.value.replace(regexp, "");
  }

  function onlyUppercase() {
    const regexp = /[^A-Z]/g; // 대문자가 아닌 모든 문자를 모두 찾아라
    console.log(event.target.value);
    event.target.value = event.target.value.replace(regexp, "");
  }

  function onlyKorean() {
    const regexp = /[^ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/g; // 한글이 아닌 모든 문자 찾기
    console.log(event.target.value);
    event.target.value = event.target.value.replace(regexp, "");
  }
</script>
```

#### 1.4.8 Scroll Event

- 스크롤시 발생하는 이벤트
- window 객체의 스크롤 y 값을 알 수 있음
  
  - ```javascript
    console.log(window.scrollY);
    ```

```html
<style>
  html {
    scroll-behavior: smooth;
  }
</style>
<body onscroll="checkScroll();">
<p>첫번째 줄</p>
<p>Paragraph</p>
<!-- 여러줄 -->
<p>Paragraph</p>
<button id="btnTop"
  style="
    position: fixed;
    bottom: 10px;
    right: 50px;
    width: 70px;
    height: 70px;
    border-radius: 35px;
    display: none;
  ">^</button>
<script>
  function myFunction() {
    console.log("scroll 이벤트");
  }

  let showScrollBtn = false;

  function checkScroll() {
    if (window.scrollY > 850 && !showScrollBtn) {
      showScrollBtn = true;
      document.querySelector("#btnTop").style.display = "";
      console.log(window.scrollY);
    } else if (window.scrollY <= 850 && showScrollBtn) {
      showScrollBtn = false;
      document.querySelector("#btnTop").style.display = "none";
      console.log(window.scrollY);
    }
  }

  window.addEventListener("load", function () {
    document
      .querySelector("#btnTop")
      .addEventListener("click", function () {
        document.documentElement.scrollTop = 0;
      });
  });
</script>
```

#### 1.4.9 Bubbling Event

- 이벤트가 발생한 노드에서 최상위 노으로 이벤트가 순차적으로 전파되는 것을 이벤트 버블링
- 다음과 같으 코드로 이벤트 버블링을 중단 할 수 있음
  - 즉, 자식-부모 요소 관계에서 두개 요소 모두 동일한 이벤트 리스너가 등록되어 있다면, 이벤트 버블링이 예측하지 못 한 이벤트 수행이 발생할 것임. 이것을 방지하기 위해서 다음의 코드와 같이 `이벤트 버블링을 중단`
  
  - ```javascript
    event.stopPropagation()
    ```

```html
<head>
  <style>
    .parent-parent {
      border: 4px dashed green;
    }

    .parent {
      border: 4px dotted blue;
    }

    .child {
      border: 4px solid red;
    }
  </style>
</head>
<body>
  <div class="parent" onclick="console.log('div 이벤트 실행')">
    <p class="child">
      p태그를 클릭해도 상위 div에 할당된 이벤트가 실행됩니다.
    </p>
  </div>
  <br />
  <br />
  <br />
  <div class="parent-parent" onclick="parentParentFunction();">
    DIV 이벤트 실행
    <div class="parent">
      div 이벤트 실행 및 버블링
      <p class="child" onclick="childFunction();">p 이벤트 실행 및 버블링</p>
    </div>
  </div>
  <script>
    // 이벤트 버블링
    // 이벤트가 발생한 노드에서 최상위 노으로 이벤트가 순차적으로 전파되는 것을 이벤트 버블링
    function childFunction() {
      console.log(event.path);
      event.stopPropagation(); // 이벤트 버블링 중지
    }

    function parentParentFunction() {
      console.log("parentParentFunction");
    }
  </script>
</body>
```

#### 1.4.10 Prevent Event

- 이벤트의 기본 동작을 중지
- 마우스 우측 클릭시 `contextmenu`(마우스 우측 버튼 클릭) 막기

```html
<script>
  // contextmenu - 마우스 우클릭
  document.addEventListener("contextmenu", function () {
    event.preventDefault(); // 이벤트의 기본 동작을 중지
  });
</script>
```

### 1.5 DOM 요소 변경

- DOM 요소를 변경하는 방법
  - `innerHTML은` HTML 태그 변경(전부)하기 위한 속성 (DOM 요소중 HTML 태그 변경)
  - `innerText는` HTML 태그 중 태그를 제외한 텍스트를 변경(전부)하기 위한 속성 (DOM 요소중 HTML 텍스트 변경)
  - `insertAdjacentHTML는` 첫번째 파라메터(추가할 위치), 두번째 파라메터(추가할 문자열) HTML 태그 변경
  - `insertAdjacentText는` 첫번째 파라메터(추가할 위치), 두번째 파라메터(추가할 문자열) HTML 텍스트 변경
    - 추가할 위치
      - beforebegin : 요소 기준으로 앞
      - afterbegin : 요소 기준으로 자식요소 앞
      - beforeend : 요소 기준으로 자식요소 뒤
      - afterend : 요소 기준으로 뒤
  - `remove` 함수를 사용해서 DOM 요소를 삭제

```html
<label for="sel">출신 지역은?</label>
<select name="" id="sel"></select>
<br />
<h1 id="title">기본 타이틀입니다.</h1>
<br />

<!-- beforebegin -->
<ul id="myUL">
  <!-- afterbegin -->
  <li>에스프레소</li>
  <li>아메리카노</li>
  <li>카라멜마끼야또</li>
  <li>오렌지주스</li>
  <li>카페라떼</li>
  <!-- beforeend -->
</ul>
<!-- afterend -->

<p id="p1">삭제할 대상 태그입니다.</p>
<script>
  // DOM 요소를 변경하는 방법
  // innerHTML - 특정 DOM 요소 안에 HTML을 전부 새로운 HTML로 변경하고 싶을 때
  // 서버로 부터 지역 목록을 가져왔다고 가정
  function setCities() {
    const cities = [
      { code: "02", text: "서울" },
      { code: "051", text: "부산" },
      { code: "064", text: "제주" },
    ];

    let optionsHTML = [];
    for (const city of cities) {
      optionsHTML.push(
        `<option value="${city.code}">${city.text}</option>`
      );
    }

    document.getElementById("sel").innerHTML = optionsHTML.join("");
  }

  // innerText - 특정 DOM 요소 안에 TEXT를 전부 새로운 TEXT로 변경하고 싶을 때
  function setTitle(title = "") {
    document.getElementById("title").innerText = title;
  }

  // insertAdjacentHTML()
  // 파라미터 2개
  // 첫번째 파라미터 - 추가하려는 위치
  // afterbegin - 접근한 DOM 요소의 자식 노드의 제일 첫번째 노드로 삽입
  // afterend - 접근한 DOM 요소 바로 다음 노드로 삽입
  // beforebegin - 접근한 DOM 요소 바로 직전 노드로 삽입
  // beforeend - 접근한 DOM 요소의 자식 노드의 제일 마지막 노드로 삽입.
  // 두번째 파라미터 - 추가할 HTML 태그에 해당하는 문자열
  function insertHTML(id, location, htmlStr) {
    document.getElementById(id).insertAdjacentHTML(location, htmlStr);
  }

  // insertAdjacentText()
  // 파라미터 2개
  // 첫번째 파라미터 - 추가하려는 위치
  // afterbegin - 접근한 DOM 요소의 자식 노드의 제일 첫번째 문자열 삽입
  // afterend - 접근한 DOM 요소 바로 다음 문자열 삽입
  // beforebegin - 접근한 DOM 요소 바로 직전 문자열 삽입
  // beforeend - 접근한 DOM 요소의 자식 노드의 제일 마지막 문자열 삽입.
  // 두번째 파라미터 - 추가할 문자열

  // remove() - DOM 요소를 삭제할 수 있음
  function removeElement(id) {
    document.getElementById(id).remove();
  }

  window.addEventListener("load", function () {
    setCities();
    setTitle("변경된 타이틀입니다.");
    insertHTML("myUL", "afterbegin", "<li>우유</li>");
    insertHTML("myUL", "beforeend", "<li>요구르트</li>");
    insertHTML(
      "myUL",
      "afterend",
      "<p>UL 태그 다음에 삽입되는 P태그입니다.</p>"
    );
    insertHTML(
      "myUL",
      "beforebegin",
      "<p>UL 태그 전에 삽입되는 P태그입니다.</p>"
    );

    setTimeout(function () {
      removeElement("p1");
    }, 5000);
  });
</script>
```

### 1.6 input validity

- 입력 유효성체크로 반드시 `form tag` 내부에 있어야 함
  - 요효성 체크 요소에는 `required` 태그로 체크 항목임을 명시
    - `form tag`의 `onsubmit` 이벤트 발생시 `자동으로 유효성 체크`하여 submit이 안됨
- 최근의 프론트앤드 프레임워크가 form tag를 사용하지 않음
  - 화면이 껌뻑이기 때문, 즉 비동기 방식으로 불가함
- 유효성 체크의 4가지 방법
  - `form` tag, `required`
  - `form` tag, `required`, `onsubmit`(event.`preventDefault`() 이벤트 막음)
  - `required`, `checkValidity`, `oninvalid`(조건이 만족되지 안을때, `setCustomValidity`() 사용)
  - 입력 요소에 `required` 속성 추가, `pattern` 속성을 정규식을 활용하여 작성

```html
<!-- 0.1 form tag, required, onsubmit을 통하여 전통적인 유요성 체크 방법 -->
<form action="">
  <div>
    <label for="email">이메일</label>
    <input type="email" name="" id="email" required />
  </div>
  <div>
    <label for="pw">비밀번호</label>
    <input type="password" name="" id="pw" required />
  </div>
  <button type="submit">로그인</button>
</form>
<br />

<!-- 0.2 onsubmit시 화면 껌뻑임(화면 전환)을 일시적으로 막아서 비동기 방식으로 구현가능 -->
<!-- onsubmit event listener에서 event.preventDefault()를 사용하여 페이지 전환 막음 -->
<form action="" onsubmit="login();">
  <div>
    <label for="email">이메일</label>
    <input type="email" name="" id="email2" required />
  </div>
  <div>
    <label for="pw">비밀번호</label>
    <input type="password" name="" id="pw2" required />
  </div>
  <div>
    <label for="pw">전화번호</label>
    <input
      type="tel"
      name=""
      id="tel"
      pattern="^010-\d{4}-\d{4}$"
      required
    />
  </div>
  <button type="submit">로그인</button>
</form>
<br />

<!-- checkValidity 함수를 사용하여  -->
<div>
  <div>
    <label for="email">이메일</label>
    <input type="email" name="" id="email3" required />
  </div>
  <div>
    <label for="pw">비밀번호</label>
    <input
      type="password"
      name=""
      id="pw3"
      oninvalid="this.setCustomValidity('비밀번호를 입력하세요.')"
      required
    />
  </div>
  <button onclick="login2();">로그인</button>
</div>
```

```javascript
// 사용자가 입력한 값이 올바른지 체크하는 방법 - 별도의 자바스크립 구현 없이
function login() {
  event.preventDefault(); // 이벤트의 기본 기능 중지
  const email = document.querySelector("#email2").value;
  const pw = document.querySelector("#pw2").value;

  // 비동기 방식으로 서버로 로그인 정보를 전송해서 로그인 처리
  // fetch()
  // 결과 처리 코드 구현
}

function login2() {
  const email = document.querySelector("#email3");
  const pw = document.querySelector("#pw3");

  // checkValidity()
  if (!email.checkValidity()) {
    return alert(email.validationMessage);
  }

  if (!pw.checkValidity()) {
    return alert(pw.validationMessage);
  }
}
```

## 2. Basic CRUD

- 실무에서 가장 기본적인 패턴을 기반으로 샘플 코드를 작성해 본다.
- 순수 자바스크립트(바닐라 자바스크립트)로 CRUD 기본 패턴 적용
- 기본 생성(Create), 조회(Read), 업데이트(Update), 삭제(Delete) 기능을 기본으로 하는 화면
  - 목록 화면
  - 생성 화면
  - 상세 화면
  - 다중 생성 화면
- 심플한 데이터 그리드
  
### 2.1 List UI

- 데이터의 목록을 표시하는 UI
- json-generator.com > 데이터 추가 (상세 방법은 [Json Server 참고](https://hong-jung.github.io/bootcamp/bootcamp-jsonServer/))
- 주요 key point
  - 검색 조건
    - gender, name(엔터키 연계)
  - 표시 항목
    - name, company, gender, email, phone, address
  - 기타
    - html 요소에 접근은 `document.querySelector(아이디)`
    - `fetch.then.then`를 사용해서 BackEnd API를 호출
    - API 호출 결과값은 `innerHTML` 속성을 사용하여 html tag를 생성하여 바인딩
    - 그리드 앞에 전체 선택/해지 체크박스 위치
    - 삭제 버튼 자동 활성/비활성
    - 
  
```html
<head>
  <style>
    .normal-table {
      border: 1px solid black;
      border-collapse: collapse;
      width: 100%;
    }

    .normal-table th,
    .normal-table td {
      border: 1px solid black;
      padding: 5px 10px;
    }

    .normal-table thead tr {
      background-color: yellow;
    }

    .striped tbody tr:nth-child(2n) {
      background-color: grey;
    }

    .hover tbody tr:hover {
      background-color: pink;
    }
  </style>
</head>

<body>
  <select name="" id="gender">
    <option value="">전체</option>
    <option value="male">남자</option>
    <option value="female">여자</option>
  </select>
  <input
    type="search"
    name=""
    id="name"
    placeholder="Name"
    onkeyup="checkEnter()"
  />
  <button onclick="doSearch();">조회</button>
  <button onclick="goToCreate();">생성</button>
  <button id="btnDelete" onclick="doDelete();" disabled>삭제</button>
  <table class="normal-table striped hover">
    <thead>
      <tr>
        <th><input type="checkbox" onchange="checkAll();" /></th>
        <th>Name</th>
        <th>Company</th>
        <th>Gender</th>
        <th>Email</th>
        <th>Phone</th>
        <th>Address</th>
      </tr>
    </thead>
    <tbody id="tbBody"></tbody>
  </table>
  <script>
    // crud - Create, Read, Update, Delete
    async function doSearch() {
      const gender = document.querySelector("#gender").value;
      const name = document.querySelector("#name").value;

      let resource = "http://localhost:3000/customers";
      if (gender === "") {
        if (name != "") {
          resource = `http://localhost:3000/customers?name_like=${name}`;
        }
      } else {
        if (name !== "") {
          resource = `http://localhost:3000/customers?gender=${gender}&name_like=${name}`;
        } else {
          resource = `http://localhost:3000/customers?gender=${gender}`;
        }
      }

      const res = await fetch(resource);
      const resJson = await res.json();
      console.log(resJson);
      renderTable(resJson);
    }

    function renderTable(data) {
      const h = [];
      for (const item of data) {
        h.push(`<tr>`);
        h.push(`<td><input type="checkbox" name="chk" value="${item.id}" onchange="isChecked();"/></td>`);
        h.push(`<td><a href="javascript:goToDetail('${item.id}');">${item.name}</a></td>`);
        h.push(`<td>${item.company}</td>`);
        h.push(`<td>${item.gender}</td>`);
        h.push(`<td>${item.email}</td>`);
        h.push(`<td>${item.phone}</td>`);
        h.push(`<td>${item.address}</td>`);
        h.push(`</tr>`);
      }

      document.querySelector("#tbBody").innerHTML = h.join("");
    }

    function goToCreate() {
      document.location.href = "60_dom_crud_create.html";
    }

    async function doDelete() {
      const chks = document.querySelectorAll("[name=chk]:checked");
      if (chks.length > 0) {
        if (confirm("정말 삭제 하시겠습니까?")) {
          for (const chk of chks) {
            await fetch(`http://localhost:3000/customers/${chk.value}`, {
              method: "DELETE",
            });
          }

          alert("데이터가 정상적으로 삭제 되었습니다.");
          doSearch();
        }
      } else {
        alert("삭제할 아이템을 선택하세요.");
      }
    }

    function checkAll() {
      console.log(event.target.checked);
      const checkValue = event.target.checked;
      const chks = document.querySelectorAll("[name=chk]");
      if (chks.length > 0) {
        for (const chk of chks) {
          chk.checked = checkValue;
        }
      }

      isChecked();
    }

    function isChecked() {
      const chks = document.querySelectorAll("[name=chk]:checked");
      if (chks.length > 0) {
        document.querySelector("#btnDelete").disabled = false;
      } else {
        document.querySelector("#btnDelete").disabled = true;
      }
    }

    function checkEnter() {
      if (event.keyCode === 13) {
        doSearch();
      }
    }

    function goToDetail(id) {
      document.location.href = `61_dom_crud_detail.html?id=${id}&v1=1&name=jeremy`;
    }
  </script>
</body>
```

### 2.2 Create UI

- 데이터를 생성하는 UI
- 주요 key point
  - name, gender, company, email, phone, address의 속성값을 저장할 수 있는 컨트롤 배치
  - 모든 속성값은 `document.querySelector(아이디).value.trim();`로 접근
  - 입력 항목들은 유효성 체크(validation)
    - `저장할때` 입력 여부 및 양식 체크
    - `onblur`(마우스 포커스 아웃) 이벤트 리스너와 `정규 표현식` 사용
    - 주소 검색을 위하여 [daum API](https://postcode.map.daum.net/guide) 사용
  - 데이터 저장은 `fetch()`로 API 호출
  - 컨트롤간 이동은 `onkeyup` 이벤트 리스너 사용

```html
<head>
  <style>
    * {
      box-sizing: border-box;
    }

    .row {
      display: flex;
      flex-wrap: wrap;
    }

    .col-4 {
      flex: 33.3333%;
      margin-bottom: 10px;
    }

    .col-8 {
      flex: 66.6666%;
      margin-bottom: 10px;
    }

    .alert {
      color: red;
    }

    input.form-control {
      width: 100%;
      padding: 5px 10px;
    }
  </style>
</head>

<body>
  <div class="row">
    <!-- name -->
    <div class="col-4">
      <label for="name">Name</label>
    </div>
    <div class="col-8">
      <input type="text" name="" id="name" class="form-control" onkeyup="checkEnter('company')" />
    </div>

    <!-- Gender -->
    <div class="col-4">
      <label for="name">Gender</label>
    </div>
    <div class="col-8">
      <input type="radio" name="gender" id="male" value="male" checked />
      <label for="male">남자</label>
      <input type="radio" name="gender" id="female" value="female" />
      <label for="female">여자</label>
    </div>

    <!-- Company -->
    <div class="col-4">
      <label for="company">Company</label>
    </div>
    <div class="col-8">
      <input type="text" name="" id="company" class="form-control" onkeyup="checkEnter('email')" />
    </div>

    <!-- Email -->
    <div class="col-4">
      <label for="email">Email</label>
    </div>
    <div class="col-8">
      <input type="email" name="" id="email" class="form-control" onblur="checkEmail();"
        onkeyup="checkEnter('phone')" />
      <div id="emailMsg" class="alert" style="display: none">
        올바른 형식의 이메일을 입력하세요.
      </div>
    </div>

    <!-- Phone -->
    <div class="col-4">
      <label for="phone">Phone</label>
    </div>
    <div class="col-8">
      <input type="tel" name="" id="phone" class="form-control" onblur="checkPhone();"
        onkeyup="checkEnter('btnDaumAPI')" />
      <div id="phoneMsg" class="alert" style="display: none">
        올바른 형식의 전화번호를 입력하세요.
      </div>
    </div>

    <!-- Address -->
    <div class="col-4">
      <label for="address">Address</label>
    </div>
    <div class="col-8">
      <button id="btnDaumAPI" onclick="openDaumAPI();">주소찾기</button>
      <input type="text" name="" id="zonecode" style="width: 80px" readonly />
      <input type="text" name="" id="address" class="form-control" readonly />
      <input type="text" name="" id="address2" class="form-control" placeholder="상세주소" onkeyup="checkEnter('create')" />
    </div>
    <div>
      <button onclick="doCreate();">생성</button>
      <button onclick="goToList();">목록</button>
    </div>
  </div>
  
  <script src="//t1.daumcdn.net/mapjsapi/bundle/postcode/prod/postcode.v2.js"></script>
  <script>
    async function doCreate() {
      const name = document.querySelector("#name").value.trim();
      const gender = document.querySelector("[name=gender]:checked").value;
      const company = document.querySelector("#company").value.trim();
      const email = document.querySelector("#email").value.trim();
      const phone = document.querySelector("#phone").value.trim();
      const address = document.querySelector("#address").value.trim();

      console.log(name);
      console.log(gender);
      console.log(company);
      console.log(email);
      console.log(phone);
      console.log(address);

      if (name === "") {
        return alert("Name을 입력하세요.");
      }

      if (company === "") {
        return alert("Company를 입력하세요.");
      }

      const regexpEmail =
        /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
      if (!regexpEmail.test(email)) {
        return alert("올바른 형식의 Email을 입력하세요.");
      }

      const regexpTel = /^010-\d{4}-\d{4}$/;
      if (!regexpTel.test(phone)) {
        return alert("올바른 형식의 Phone을 입력하세요.");
      }

      if (address === "") {
        return alert("Address를 입력하세요.");
      }

      const zonecode = document.querySelector("#zonecode").value;
      const address2 = document.querySelector("#address2").value;

      if (confirm("정말 저장하시겠습니까?")) {
        const res = await fetch("http://localhost:3000/customers", {
          method: "POST",
          body: JSON.stringify({
            name,
            gender,
            company,
            email,
            phone,
            address: `(${zonecode})${address} ${address2}`.trim(),
            zonecode: zonecode,
            roadAddress: address,
            address2: address2,
          }),
          headers: {
            "content-type": "application/json;charset=UTF-8",
          },
        });

        if (res.status === 201) {
          alert("정상적으로 생성되었습니다.");
        } else {
          alert("고객 정보를 생성하지 못했습니다. 다시 시도하세요.");
        }
      }
    }

    function checkEmail() {
      const email = document.querySelector("#email").value;
      if (email !== "") {
        const regexpEmail =
          /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
        if (!regexpEmail.test(email)) {
          document.querySelector("#emailMsg").style.display = "";
        } else {
          document.querySelector("#emailMsg").style.display = "none";
        }
      } else {
        document.querySelector("#emailMsg").style.display = "none";
      }
    }

    function checkPhone() {
      const phone = document.querySelector("#phone").value;
      if (phone !== "") {
        const regexpTel = /^010-\d{4}-\d{4}$/;
        if (!regexpTel.test(phone)) {
          document.querySelector("#phoneMsg").style.display = "";
        } else {
          document.querySelector("#phoneMsg").style.display = "none";
        }
      } else {
        document.querySelector("#phoneMsg").style.display = "none";
      }
    }

    function openDaumAPI() {
      new daum.Postcode({
        oncomplete: function (data) {
          // 팝업에서 검색결과 항목을 클릭했을때 실행할 코드를 작성하는 부분입니다.
          // 예제를 참고하여 다양한 활용법을 확인해 보세요.
          console.log(data);
          document.querySelector("#zonecode").value = data.zonecode;
          document.querySelector("#address").value = data.roadAddress;
        },
      }).open();
    }

    function checkEnter(moveId) {
      if (event.keyCode === 13) {
        if (moveId === "btnDaumAPI") {
          openDaumAPI();
        } else if (moveId === "create") {
          doCreate();
        } else {
          document.querySelector("#" + moveId).focus();
        }
      }
    }

    function goToList() {
      document.location.href = "59_dom_crud_list.html";
    }
  </script>
</body>
```

### 2.3 Detail UI

- 목록 페이지의 이름을 클릭시 상세 페이지로 이동
- 이동시 queryString을 통하여 전달된 파라메터를 파싱하여 사용
  
```javascript
//호출하는 함수
function goToDetail(id) {
    document.location.href = `61_dom_crud_detail.html?id=${id}&v1=1&name=jeremy`;
}

//queryString 받는 함수
function parseQueryString() {
    const queryString = window.location.search.substring(1).split("&");
    console.log(queryString);
}
```

```javascript
/**
 * 이 함수는 제품 가격에 대한 부가세를 계산해서 반환하는 함수입니다.
 * @param {*} productAmount 제품가격을 숫자형 전달
 * @returns 부가세가 숫자형
 */
function taxAmount(productAmount) {
  // 부가세 10% 가정
  const tax = 0.1;
  return productAmount * tax;
}

function getTop5() {
  return [];
}

function parseQueryString() {
  if (window.location.search.length === 0) {
    return {};
  } else {
    const queryStringObject = {};
    const queryString = window.location.search.substring(1).split("&");
    console.log(queryString);
    for (const s of queryString) {
      const q = s.split("=");
      queryStringObject[q[0]] = q[1];
    }

    console.log(queryStringObject);
    return queryStringObject;
  }
}
```

```html
<head>
  <style>
    * {
      box-sizing: border-box;
    }

    .row {
      display: flex;
      flex-wrap: wrap;
    }

    .col-4 {
      flex: 33.3333%;
      margin-bottom: 10px;
    }

    .col-8 {
      flex: 66.6666%;
      margin-bottom: 10px;
    }

    .alert {
      color: red;
    }

    input.form-control {
      width: 100%;
      padding: 5px 10px;
    }
  </style>
</head>
<body>
  <div class="row">
    <!-- Name -->
    <div class="col-4">
      <label for="name">Name</label>
    </div>
    <div class="col-8"><span id="name"></span></div>

    <!-- Gender -->
    <div class="col-4">
      <label for="name">Gender</label>
    </div>
    <div class="col-8"><span id="gender"></span></div>

    <!-- Company -->
    <div class="col-4">
      <label for="company">Company</label>
    </div>
    <div class="col-8"><span id="company"></span></div>

    <!-- Email -->
    <div class="col-4">
      <label for="email">Email</label>
    </div>
    <div class="col-8"><span id="email"></span></div>

    <!-- Phone -->
    <div class="col-4">
      <label for="phone">Phone</label>
    </div>
    <div class="col-8"><span id="phone"></span></div>

    <!-- Address -->
    <div class="col-4">
      <label for="address">Address</label>
    </div>
    <div class="col-8"><span id="address"></span></div>

    <div>
      <button onclick="goToUpdate();">수정</button>
      <button onclick="goToList();">목록</button>
    </div>
  </div>

  <script src="./js/common.js"></script>
  <script>
    async function doSearchDetail() {
      const { id } = parseQueryString();
      const res = await fetch(`http://localhost:3000/customers/${id}`);
      const resJson = await res.json();
      console.log(resJson);
      renderDetail(resJson);
    }

    function renderDetail(data) {
      document.querySelector("#name").innerText = data.name;
      document.querySelector("#gender").innerText = data.gender;
      document.querySelector("#company").innerText = data.company;
      document.querySelector("#email").innerText = data.email;
      document.querySelector("#phone").innerText = data.phone;
      document.querySelector("#address").innerText = data.address;
    }

    function goToList() {
      document.location.href = "59_dom_crud_list.html";
    }

    function goToUpdate() {
      const { id } = parseQueryString();
      document.location.href = `62_dom_crud_update.html?id=${id}`;
    }

    doSearchDetail();
  </script>
</body>
```

### 2.4 Update UI

- 생성 UI를 재활용 함으로 생성 UI를 초기에 가장 완성도 높게 만들어야 한다.
- 상세 UI에서 ID를 파라메터로 수정 UI로 전달하며, 전달받은 ID를 기준으로 생성 화면과 동일하게 구성 한다.

```html
<head>
  <style>
    * {
      box-sizing: border-box;
    }

    .row {
      display: flex;
      flex-wrap: wrap;
    }

    .col-4 {
      flex: 33.3333%;
      margin-bottom: 10px;
    }

    .col-8 {
      flex: 66.6666%;
      margin-bottom: 10px;
    }

    .alert {
      color: red;
    }

    input.form-control {
      width: 100%;
      padding: 5px 10px;
    }
  </style>
</head>
<body>
  <div class="row">
    <div class="col-4">
      <label for="name">Name</label>
    </div>
    <div class="col-8">
      <input
        type="text"
        name=""
        id="name"
        class="form-control"
        onkeyup="checkEnter('company')"
      />
    </div>
    <div class="col-4">
      <label for="name">Gender</label>
    </div>
    <div class="col-8">
      <input type="radio" name="gender" id="male" value="male" checked />
      <label for="male">남자</label>
      <input type="radio" name="gender" id="female" value="female" />
      <label for="female">여자</label>
    </div>
    <div class="col-4">
      <label for="company">Company</label>
    </div>
    <div class="col-8">
      <input
        type="text"
        name=""
        id="company"
        class="form-control"
        onkeyup="checkEnter('email')"
      />
    </div>
    <div class="col-4">
      <label for="email">Email</label>
    </div>
    <div class="col-8">
      <input
        type="email"
        name=""
        id="email"
        class="form-control"
        onblur="checkEmail();"
        onkeyup="checkEnter('phone')"
      />
      <div id="emailMsg" class="alert" style="display: none">
        올바른 형식의 이메일을 입력하세요.
      </div>
    </div>
    <div class="col-4">
      <label for="phone">Phone</label>
    </div>
    <div class="col-8">
      <input
        type="tel"
        name=""
        id="phone"
        class="form-control"
        onblur="checkPhone();"
        onkeyup="checkEnter('btnDaumAPI')"
      />
      <div id="phoneMsg" class="alert" style="display: none">
        올바른 형식의 전화번호를 입력하세요.
      </div>
    </div>
    <div class="col-4">
      <label for="address">Address</label>
    </div>
    <div class="col-8">
      <button id="btnDaumAPI" onclick="openDaumAPI();">주소찾기</button>
      <input type="text" name="" id="zonecode" style="width: 80px" readonly />
      <input type="text" name="" id="address" class="form-control" readonly />
      <input
        type="text"
        name=""
        id="address2"
        class="form-control"
        placeholder="상세주소"
        onkeyup="checkEnter('create')"
      />
    </div>
    <div>
      <button onclick="doSave();">저장</button>
      <button onclick="goToList();">목록</button>
    </div>
  </div>
  <script src="//t1.daumcdn.net/mapjsapi/bundle/postcode/prod/postcode.v2.js"></script>
  <script src="./js/common.js"></script>
  <script>
    async function doSearchDetail() {
      const { id } = parseQueryString();
      const res = await fetch(`http://localhost:3000/customers/${id}`);
      const resJson = await res.json();
      console.log(resJson);
      renderDetail(resJson);
    }

    function renderDetail(data) {
      document.querySelector("#name").value = data.name;
      document.querySelector("#" + data.gender).checked = true;
      document.querySelector("#company").value = data.company;
      document.querySelector("#email").value = data.email;
      document.querySelector("#phone").value = data.phone;
      document.querySelector("#address").value = data.roadAddress;
      document.querySelector("#address2").value = data.address2;
      document.querySelector("#zonecode").value = data.zonecode;
    }

    doSearchDetail();

    async function doSave() {
      const name = document.querySelector("#name").value.trim();
      const gender = document.querySelector("[name=gender]:checked").value;
      const company = document.querySelector("#company").value.trim();
      const email = document.querySelector("#email").value.trim();
      const phone = document.querySelector("#phone").value.trim();
      const address = document.querySelector("#address").value.trim();

      console.log(name);
      console.log(gender);
      console.log(company);
      console.log(email);
      console.log(phone);
      console.log(address);

      if (name === "") {
        return alert("Name을 입력하세요.");
      }

      if (company === "") {
        return alert("Company를 입력하세요.");
      }

      const regexpEmail =
        /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
      if (!regexpEmail.test(email)) {
        return alert("올바른 형식의 Email을 입력하세요.");
      }

      const regexpTel = /^010-\d{4}-\d{4}$/;
      if (!regexpTel.test(phone)) {
        return alert("올바른 형식의 Phone을 입력하세요.");
      }

      if (address === "") {
        return alert("Address를 입력하세요.");
      }

      const zonecode = document.querySelector("#zonecode").value;
      const address2 = document.querySelector("#address2").value;

      const { id } = parseQueryString();

      if (confirm("정말 저장하시겠습니까?")) {
        const res = await fetch(`http://localhost:3000/customers/${id}`, {
          method: "PUT",
          body: JSON.stringify({
            name,
            gender,
            company,
            email,
            phone,
            address: `(${zonecode})${address} ${address2}`.trim(),
            zonecode: zonecode,
            roadAddress: address,
            address2: address2,
          }),
          headers: {
            "content-type": "application/json;charset=UTF-8",
          },
        });

        if (res.status === 200) {
          alert("정상적으로 저장되었습니다.");
        } else {
          alert("고객 정보를 저장하지 못했습니다. 다시 시도하세요.");
        }
      }
    }

    function checkEmail() {
      const email = document.querySelector("#email").value;
      if (email !== "") {
        const regexpEmail =
          /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
        if (!regexpEmail.test(email)) {
          document.querySelector("#emailMsg").style.display = "";
        } else {
          document.querySelector("#emailMsg").style.display = "none";
        }
      } else {
        document.querySelector("#emailMsg").style.display = "none";
      }
    }

    function checkPhone() {
      const phone = document.querySelector("#phone").value;
      if (phone !== "") {
        const regexpTel = /^010-\d{4}-\d{4}$/;
        if (!regexpTel.test(phone)) {
          document.querySelector("#phoneMsg").style.display = "";
        } else {
          document.querySelector("#phoneMsg").style.display = "none";
        }
      } else {
        document.querySelector("#phoneMsg").style.display = "none";
      }
    }

    function openDaumAPI() {
      new daum.Postcode({
        oncomplete: function (data) {
          // 팝업에서 검색결과 항목을 클릭했을때 실행할 코드를 작성하는 부분입니다.
          // 예제를 참고하여 다양한 활용법을 확인해 보세요.
          console.log(data);
          document.querySelector("#zonecode").value = data.zonecode;
          document.querySelector("#address").value = data.roadAddress;
        },
      }).open();
    }

    function checkEnter(moveId) {
      if (event.keyCode === 13) {
        if (moveId === "btnDaumAPI") {
          openDaumAPI();
        } else if (moveId === "create") {
          doCreate();
        } else {
          document.querySelector("#" + moveId).focus();
        }
      }
    }

    function goToList() {
      document.location.href = "59_dom_crud_list.html";
    }
  </script>
</body>
```
  
### 2.5 Multiple Create UI

- 목록 UI에서 바로 데이터를 등록
- 라인추가, 라인삭제 관련된 validation
- 추가되어 선택된 행에 대해서 데이터 저장

```html
<head>
  <style>
    .normal-table {
      border: 1px solid black;
      border-collapse: collapse;
      width: 100%;
    }

    .normal-table th,
    .normal-table td {
      border: 1px solid black;
      padding: 5px 10px;
    }

    .normal-table thead tr {
      background-color: yellow;
    }

    .striped tbody tr:nth-child(2n) {
      background-color: grey;
    }

    .hover tbody tr:hover {
      background-color: pink;
    }
  </style>
</head>
<body>
  <div style="margin-bottom: 5px">
    <button id="btnSave" onclick="doSave();" disabled>저장</button>
    <button onclick="addLine();">라인추가</button>
    <button id="btnRemove" onclick="removeLine();" disabled>라인삭제</button>
  </div>
  <table class="normal-table">
    <thead>
      <tr>
        <th><input type="checkbox" onchange="checkAll();" /></th>
        <th>Name</th>
        <th>Company</th>
        <th>Gender</th>
        <th>Email</th>
        <th>Phone</th>
        <th>Address</th>
      </tr>
    </thead>
    <tbody id="tbBody"></tbody>
  </table>
  <script>
    function addLine() {
      const h = [];
      h.push(`<tr>`);
      h.push(
        `<td><input type="checkbox" name="chk" onchange="isChecked();" /></td>`
      );
      h.push(`<td><input type="text" name="name" /></td>`);
      h.push(`<td><input type="text" name="company" /></td>`);
      h.push(
        `<td><select name="gender"><option value="male" selected>남자</option><option value="female">여자</option></select></td>`
      );
      h.push(`<td><input type="text" name="email" /></td>`);
      h.push(`<td><input type="text" name="phone" /></td>`);
      h.push(`<td><input type="text" name="address" /></td>`);
      h.push(`</tr>`);

      document
        .querySelector("#tbBody")
        .insertAdjacentHTML("beforeend", h.join(""));
    }

    function removeLine() {
      const chks = document.querySelectorAll("[name=chk]:checked");
      if (chks.length > 0) {
        chks.forEach((chk) => {
          let tr = chk; // INPUT
          while (tr.tagName !== "TR") {
            tr = tr.parentNode; // 바로 부모 노드를 가져옴.
          }

          tr.remove();
        });
      }
    }

    function checkAll() {
      console.log(event.target.checked);
      const checkValue = event.target.checked;
      const chks = document.querySelectorAll("[name=chk]");
      if (chks.length > 0) {
        for (const chk of chks) {
          chk.checked = checkValue;
        }
      }

      isChecked();
    }

    function isChecked() {
      const chks = document.querySelectorAll("[name=chk]:checked");
      if (chks.length > 0) {
        document.querySelector("#btnRemove").disabled = false;
        document.querySelector("#btnSave").disabled = false;
      } else {
        document.querySelector("#btnRemove").disabled = true;
        document.querySelector("#btnSave").disabled = true;
      }
    }

    async function doSave() {
      const chks = document.querySelectorAll("[name=chk]");

      if (chks.length > 0) {
        let passRequired = true;
        const blankRows = [];
        let passEmail = true;
        const wrongEmails = [];
        let passPhone = true;
        const wrongPhones = [];
        const customers = [];

        const regexpEmail =
          /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
        const regexpTel = /^010-\d{4}-\d{4}$/;
        chks.forEach((chk, index) => {
          if (chk.checked) {
            let tr = chk;
            while (tr.tagName !== "TR") {
              tr = tr.parentNode; // 바로 부모 노드를 가져옴.
            }

            const name = tr.querySelectorAll("[name=name]")[0].value;
            const company = tr.querySelectorAll("[name=company]")[0].value;
            const gender = tr.querySelectorAll("[name=gender]")[0].value;
            const email = tr.querySelectorAll("[name=email]")[0].value;
            const phone = tr.querySelectorAll("[name=phone]")[0].value;
            const address = tr.querySelectorAll("[name=address]")[0].value;

            customers.push({
              name,
              company,
              gender,
              email,
              phone,
              address,
            });

            if (
              name === "" ||
              company === "" ||
              email === "" ||
              phone === "" ||
              address === ""
            ) {
              passRequired = false;
              blankRows.push(index + 1);
            }

            if (!regexpEmail.test(email)) {
              passEmail = false;
              wrongEmails.push(index + 1);
            }

            if (!regexpTel.test(phone)) {
              passPhone = false;
              wrongPhones.push(index + 1);
            }
          }
        });

        if (!passRequired) {
          return alert(
            `${blankRows.join(
              ","
            )}행에 비어 있는 값이 존재합니다. 모든 값을 입력하세요.`
          );
        }

        if (!passEmail) {
          return alert(
            `${wrongEmails.join(
              ","
            )}행에 입력한 이메일 형식이 올바르지 않습니다.`
          );
        }

        if (!passPhone) {
          return alert(
            `${wrongPhones.join(
              ","
            )}행에 입력한 전화번호 형식이 올바르지 않습니다.`
          );
        }

        const failData = [];
        if (confirm("정말 저장하시겠습니까?")) {
          for (const customer of customers) {
            const res = await fetch("http://localhost:3000/customers", {
              method: "POST",
              body: JSON.stringify(customer),
              headers: {
                "content-type": "application/json;charset=UTF-8",
              },
            });

            if (res.status !== 201) {
              failData.push(customer);
            }
          }

          if (failData.length > 0) {
            alert(`저장에 실패한 데이터가 ${failData.length}건 있습니다.`);
          } else {
            alert("정상적으로 저장 되었습니다.");
          }
        }
      }
    }
  </script>
</body>
```

### 2.6 Simple Data Grid

- contents

## 3. Additional

### 3.1 LocalStorage & SessionStorage

- contents

### 3.2 GeoLocation API

- [Geolocation MDN Developer](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)
- [Javascript Distance](https://www.geodatasource.com/developers/javascript)
- [Javascript Sort by key](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
- 특정 목적지 목록을 기준으로 사용자가 접속한 위치와 비교하여 가까운 순서로 정렬

```html
<body>
  <script>
    let tourList = [
      {name:"오설록", addr:"제주시", latitude:33.3012, longitude:126.12231},
      {name:"섭지코지", addr:"제주시", latitude:33.4302, longitude:126.2213},
    ];

    //https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API
    //navigator.geolocation.getCurrentPosition(showLocation, errorHandler);
    navigator.geolocation.getCurrentPosition((position) => {
      let latitude = position.coords.latitude;
      let longitude = position.coords.longitude;

      console.log('latitude : ', latitude);
      console.log('longitude : ', longitude);

      for(let i=0; i<tourList.length; i++){
        let distance = getDistance(latitude, longitude, tourList[i].latitude, tourList[i].longitude, "K");
        tourList[i].distance = distance;
      }

      //https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
      let newTourList = tourList.sort(function (a, b) {
        if (a.distance > b.distance) {
          return 1;
        }
        if (a.distance < b.distance) {
          return -1;
        }
        // a must be equal to b
        return 0;
      });

      console.log(newTourList);
    }, (err) => {

    });

    //https://www.geodatasource.com/developers/javascript
    function getDistance(lat1, lon1, lat2, lon2, unit) {
      if ((lat1 == lat2) && (lon1 == lon2)) {
        return 0;
      }
      else {
        var radlat1 = Math.PI * lat1/180;
        var radlat2 = Math.PI * lat2/180;
        var theta = lon1-lon2;
        var radtheta = Math.PI * theta/180;
        var dist = Math.sin(radlat1) * Math.sin(radlat2) + Math.cos(radlat1) * Math.cos(radlat2) * Math.cos(radtheta);
        if (dist > 1) {
          dist = 1;
        }
        dist = Math.acos(dist);
        dist = dist * 180/Math.PI;
        dist = dist * 60 * 1.1515;
        if (unit=="K") { dist = dist * 1.609344 }
        if (unit=="N") { dist = dist * 0.8684 }
        return dist;
      }
    }
  </script>
</body>
```

### 3.3 Web Speech API

- [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API/Using_the_Web_Speech_API)
- `크롬`이 `엣지` 브라우저의 경우 호환
- `영문만 가능`하며, 영문의 음성을 텍스트로 인식하여 배열로 반환
- 텍스트 입력이 불편할 경우 활용가능

```html
<body>
  <input type="text" id="speechResult" />
  <button type="button" onclick="startSpeechRecognition();">Start Record</button>
  <button type="button" onclick="endSpeechRecognition();">End Record</button>
  <script>
    let recognition = null;
    function checkCompatibility() {
      recognition = new(window.SpeechRecognition || window.webkitSpeechRecognition) ();
      recognition.lang = "en";
      recognition.maxAlternatives = 5;

      if(!recognition) {
        alert("you cannot use speech api.");
      }
    }

    function startSpeechRecognition() {
      console.log('start');

      recognition.addEventListener("speechstart", () => {
        console.log('speech start');
      });

      recognition.addEventListener("speechend", () => {
        console.log('speech end');
      });

      recognition.addEventListener("result", (event) => {
        console.log('speech result : ', event.results);
        const text = event.results[0][0].transcript;
        document.getElementById("speechResult").value = text;
      });

      recognition.start();
    }

    function endSpeechRecognition() {
      recognition.stop();
    }

    window.addEventListener('load', checkCompatibility);
  </script>
</body>
```

## 4. 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)
   NOTE, TIP, IMPORTANT, CAUTION, and WARNING.
  
>[!IMPORTANT]
>
> NOTE, TIP, IMPORTANT, CAUTION, ALERT and WARNING.<br>
>~~important~~<br>
><u>importtant</u><br>
>important