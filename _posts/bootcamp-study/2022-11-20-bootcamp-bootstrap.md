---
title:  "Bootstrap"
excerpt: "개발자의품격"
comments: true
header:

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, bootstrap]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-11-20
last_modified_at: 2022-11-20
---

- [1. What is bootstrap](#1-what-is-bootstrap)
  - [생성](#생성)
  - [상세](#상세)
  - [수정](#수정)
  - [삭제](#삭제)
  - [멀티생성](#멀티생성)
- [10. Theme](#10-theme)
- [참고](#참고)

# 1. What is bootstrap

<img src="https://getbootstrap.com/docs/5.2/assets/img/bootstrap-icons@2x.png" width="100%" align="center"/>

- [Bootstrap 공식 사이트](https://getbootstrap.com/)

> **IMPORTANT**
>> 가장 많이 사용 "**<u>반응형 웹 프론트앤드 디자인 툴 킷</u>**"<br>
>>
>> - html, css, javascript 를 이용한 화면을 일정수순 이상의 품질을 보장해주는 웹 화면을 구성을 도와주는 오픈소스 프레임워크<br>
>> - 다양한 디바이스에 최적의 웹 레이아웃에 최적화되어 있어 많이 사용하며, 자주 사용하는 위젯과 콤포넌트가 이미 만들어져 있음<br>
>> - Bootstrap CSS & JavaScript CDN 추가 ([bootstrap getting started](https://getbootstrap.com/docs/5.2/getting-started/introduction/))

- ```html
  <!-- CSS CDN -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">

  <!-- Javascript CDN -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3"
        crossorigin="anonymous"></script>
  ```

# 2. Layout

- 반응형 웹에 대한 모든 요소
  - `brakpoints`, `containers`, `grid` 가장 중요한 개념
- `Breakpoints` (**해상도별 크기 기준**)
  - 디바이스별 반응형의 작동 방식 (사용자 해상도 넓이에 따른 기준)
  - [bootstrap layout](https://getbootstrap.com/docs/5.2/layout/breakpoints/)

| breakpoint        | class infix | dimensions  |
| :---------------- | :---------- | :---------- |
| X-Small           | None        | < `576px`   |
| Small             | sm          | >= 576px    |
| Medium            | md          | >= `768px`  |
| Large             | lg          | >= `992px`  |
| Extra large       | xl          | >= `1200px` |
| Extra extra large | xxl         | >= `1400px` |

- `Containers` (**기본 블록, 중앙에 위치 시킨다**)
  - bootstrap을 만들기 위한 가장 기본 요소 (부트스트랩의 기본 빌딩 블록)
  - [bootstrap containers](https://getbootstrap.com/docs/5.2/layout/containers/)
  - 화면의 해상도에 따라서 넓이를 100% 잡을 것인지 각 크기별로 다르게 줄것인지 결정

- `Grid` (**12 Grid**)
  - [bootstrap grid system](https://getbootstrap.com/docs/5.2/layout/grid/)
  - 화면의 해상도에 컬럼을 12개로 나눈다. (12 grid system 이라고 부른다.)

  - ```html
    <div class="container">
        <div class="row">
            <div class="col">
                Column
            </div>
            <div class="col">
                Column
            </div>
            <div class="col">
                Column
            </div>
        </div>
    </div>

    <div class="row">
        <!-- 
        col-sm-12 : 해상도 sm(≥576px)일때 12 그리드 중 1 col = 12. 즉, row 당 1 col 표시
        col-md-6 : 해상도 md(≥768px)일때 12 그리드 중 1 col = 6. 즉, row 당 2 col 표시
        col-lg-4 : 해상도 lg(≥992px)일때 12 그리드 중 1 col = 4. 즉, row 당 3 col 표시
        col-xl-3 : 해상도 xl(≥1200px)일때 12 그리드 중 1 col = 3. 즉, row 당 4 col 표시
        -->
        <div class="col-md-6 col-lg-4 col-xl-3">A</div>
        <div class="col-md-6 col-lg-4 col-xl-3">B</div>
        <div class="col-md-6 col-lg-4 col-xl-3">C</div>
        <div class="col-md-6 col-lg-4 col-xl-3">D</div>
        <div class="col-md-6 col-lg-4 col-xl-3">E</div>
        <div class="col-md-6 col-lg-4 col-xl-3">F</div>
        <div class="col-md-6 col-lg-4 col-xl-3">G</div>
        <div class="col-md-6 col-lg-4 col-xl-3">H</div>
    </div>
    ```

- Columns
  - [bootstrap column](https://getbootstrap.com/docs/5.2/layout/columns/)
  - 컬럼의 정렬(가로, 세로), 배치
- Gutters
  - [bootstrap gutters](https://getbootstrap.com/docs/5.2/layout/gutters/)
  - 그리드 시스템내에서의 간격 조정
  - 컬럼(column)과 컬럼(column)사이의 패딩(padding, 간격) 조정
  - 행(row)과 행(row)사이의 패딩(padding, 간격) 조정
- Utilities
  - [bootstrap utilities](https://getbootstrap.com/docs/5.2/layout/utilities/)
  - 디스플레이(display) - 보이게 말거냐? 포지션
  - 플랙스박스(flexbox) 관련 속성
  - 마진(margin), 패딩(padding) 관련 속성
  - 토글(toggle) 속성
  - 브레이크포인트(breakpoints)를 사용하여 해상도별로 숨김/나타남 처리 유틸리티 유용함
  - z-index
    - 컨텐츠를 포토샵의 레이어처럼 위쪽으로 살짝 올리는 값에 대한 기준
  - CSS grid
    - flexbox(1차원), grid(2차원)

# 3. Content

- Reboot, Typography, Images, Tables, Figures

| name       | class name                                                       | description                                                                                       |
| :--------- | :--------------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| Typography | h1~6, mark, del, s, ins, u, strong, em                           | [글자 관련된 디자인 클래스](https://getbootstrap.com/docs/5.2/content/typography/)                |
| Images     | img-fluid, img-thumbnail                                         | [이미지 관련된 디자인](https://getbootstrap.com/docs/5.2/content/images/)                         |
| Tables     | table, table-primary, table-striped, table-hover, table-bordered | [테이블(table) 태그(tag)에 대한 디자인 클래스](https://getbootstrap.com/docs/5.2/content/tables/) |

# 4. Forms

- 입력 관련 컨트롤에 대한 디자인 스타일 제공

| name            | class name                                                                                               | description                                                                                                       |
| :-------------- | :------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------- |
| From control    | form-label, form-control, disabled readonly                                                              | [type='text'와 같은 기본 입력 컨트롤](https://getbootstrap.com/docs/5.2/forms/form-control/)                      |
| Select          | form-select,                                                                                             | [선택 컨트롤](https://getbootstrap.com/docs/5.2/forms/select/)                                                    |
| Check & Radios  | form-check-input, form-check-label, class="form-check form-switch", class="form-check form-check-inline" | [체크 및 라디오](https://getbootstrap.com/docs/5.2/forms/checks-radios/)                                          |
| Range           | form-range                                                                                               | [범위](https://getbootstrap.com/docs/5.2/forms/range/)                                                            |
| Input group     | div / class="input-group", span / class="input-group-text"                                               | [입력 컨트롤의 그룹핑](https://getbootstrap.com/docs/5.2/forms/input-group/)                                      |
| Floating labels | div / class="form-floating"                                                                              | [라벨과 입력을 한개의 그룹으로 묶고 라벨을 플로팅 시킴](https://getbootstrap.com/docs/5.2/forms/floating-labels/) |
| Layout          |                                                                                                          | [layout 패턴 및 스타일](https://getbootstrap.com/docs/5.2/forms/layout/)                                          |
| Validation      | needs-validation, valid-feedback , invalid-feedback                                                      | [유효성 검사](https://getbootstrap.com/docs/5.2/forms/validation/)                                                |

# 5. Components

- 간략한 설명

| name         | class name                               | description                                                                           |
| :----------- | :--------------------------------------- | :------------------------------------------------------------------------------------ |
| Accordion    | accordion-xx                             | [확장, 축소 컨트롤](https://getbootstrap.com/docs/5.2/components/accordion/)          |
| Alerts       | alert                                    | [알람](https://getbootstrap.com/docs/5.2/components/alerts/)                          |
| Badge        | badge                                    | [뱃지 카운트, 마크](https://getbootstrap.com/docs/5.2/components/badge/)              |
| Breadcrumb   | breadcrumb                               | [메뉴 네비게이션](https://getbootstrap.com/docs/5.2/components/breadcrumb/)           |
| Buttons      | btn                                      | [버튼 스타일](https://getbootstrap.com/docs/5.2/components/buttons/)                  |
| Button group | btn-group                                | [버튼의 그룹화](https://getbootstrap.com/docs/5.2/components/button-group/)           |
| Card         | card-xx                                  | [카드 스타일](https://getbootstrap.com/docs/5.2/components/card/)                     |
| Carousel     | carousel-xx                              | [이미지 스라이딩](https://getbootstrap.com/docs/5.2/components/carousel/)             |
| Close button | btn-close                                | [닫힘 버튼](https://getbootstrap.com/docs/5.2/components/close-button/)               |
| Collapse     | collapse, data-bs-toggle, data-bs-target | [확장, 축소](https://getbootstrap.com/docs/5.2/components/collapse/)                  |
| Dropdowns    | dropdown                                 | [메뉴의 서브메뉴](https://getbootstrap.com/docs/5.2/components/dropdowns/)            |
| List group   | list-group-xx                            | [정형화된 목록](https://getbootstrap.com/docs/5.2/components/list-group/)             |
| Modal        | modal-xx, static backdrop                | [팝업창](https://getbootstrap.com/docs/5.2/components/modal/)                         |
| Navbar       | navbar-xx                                | [메뉴](https://getbootstrap.com/docs/5.2/components/navbar/)                          |
| Navs & tabs  | nav-xx                                   | [Nav + Tab](https://getbootstrap.com/docs/5.2/components/navs-tabs/)                  |
| Offcanvas    | offcanvas-xx                             | [스라이딩 캔버스](https://getbootstrap.com/docs/5.2/components/offcanvas/)            |
| Pagination   | Page, pagination                         | [페이징](https://getbootstrap.com/docs/5.2/components/pagination/)                    |
| Placeholders | placeholder                              | [로딩 효과](https://getbootstrap.com/docs/5.2/components/placeholders/)               |
| Popovers     | data-bs-toggle, popover                  | [클릭이나 이벤트시 설명 문구](https://getbootstrap.com/docs/5.2/components/popovers/) |
| Progress     | progress-xx                              | [진행상태](https://getbootstrap.com/docs/5.2/components/progress/)                    |
| Scrollspy    | data-bs-spy, scroll                      | [스크롤 이동](https://getbootstrap.com/docs/5.2/components/scrollspy/)                |
| Spinners     | spinner-border                           | [스핀-로딩](https://getbootstrap.com/docs/5.2/components/spinners/)                   |
| Toasts       | toast-xx                                 | [잠깐 보였다 사라지는 알람](https://getbootstrap.com/docs/5.2/components/toasts/)     |
| Tooltips     | data-bs-toggle="tooltip"                 | [툴팁](https://getbootstrap.com/docs/5.2/components/tooltips/)                        |

# 6. Helpers

- 다양한 Helper 

| name               | class name                      | description                                                                  |
| :----------------- | :------------------------------ | :--------------------------------------------------------------------------- |
| Clearfix           | clearfix,float-start, float-end | [Bootstrap Refer](https://getbootstrap.com/docs/5.2/helpers/clearfix/)       |
| Color & background | text-bg-xx                      | [색상, 배경색](https://getbootstrap.com/docs/5.2/helpers/color-background/)  |
| Colored links      | link-xx                         | [링크 스타일](https://getbootstrap.com/docs/5.2/helpers/colored-links/)      |
| Position           | fixed-xx, sticky-xx             | [위치 관련 스타일](https://getbootstrap.com/docs/5.2/helpers/position/)      |
| Ratio              | ratio-xx                        | [동영상 이미지 비율](https://getbootstrap.com/docs/5.2/helpers/ratio/)       |
| Stacks             | vstack, hstack                  | [세로, 가로 쌓기](https://getbootstrap.com/docs/5.2/helpers/stacks/)         |
| Stretched link     |                                 | [Bootstrap Refer](https://getbootstrap.com/docs/5.2/helpers/stretched-link/) |
| Text truncation    | text-truncate                   | [글자 줄임표시](https://getbootstrap.com/docs/5.2/helpers/text-truncation/)  |
| Vertical rule      | vr                              | [세로 구분자](https://getbootstrap.com/docs/5.2/helpers/vertical-rule/)      |
| Visually hidden    | visually-xx                     | [숨김](https://getbootstrap.com/docs/5.2/helpers/visually-hidden/)           |

# 7. Utilities

- 다양한 Utilities

| name           | class name               | description                                                                   |
| :------------- | :----------------------- | :---------------------------------------------------------------------------- |
| API            | SASS                     | [Bootstrap Refer](https://getbootstrap.com/docs/5.2/utilities/api/)           |
| Background     | bg-xx                    | [배경색](https://getbootstrap.com/docs/5.2/utilities/background/)             |
| Borders        | border-xx                | [Border](https://getbootstrap.com/docs/5.2/utilities/borders/)                |
| Colors         | text-xx, text-opacity-xx | [글자색, 투명도](https://getbootstrap.com/docs/5.2/utilities/colors/)         |
| Display        | d-{brakpoint}-{value}    | [표시](https://getbootstrap.com/docs/5.2/utilities/display/)                  |
| Flex           | d-flex, flex-xx          | [flex layout](https://getbootstrap.com/docs/5.2/utilities/flex/)              |
| Float          | float-xx                 | [float](https://getbootstrap.com/docs/5.2/utilities/float/)                   |
| Interactions   | user-select-xx           | [text 선택 스타일](https://getbootstrap.com/docs/5.2/utilities/interactions/) |
| Opacity        | opacity-xx               | [투명도](https://getbootstrap.com/docs/5.2/utilities/opacity/)                |
| Overflow       | overflow-xx              | [overflow 스타일](https://getbootstrap.com/docs/5.2/utilities/overflow/)      |
| Position       | position-xx              | [position 스타일](https://getbootstrap.com/docs/5.2/utilities/position/)      |
| Shadows        | shadow-xx                | [그림자](https://getbootstrap.com/docs/5.2/utilities/shadows/)                |
| Sizing         | w-xx, h-xx               | [넓이, 높이 크기](https://getbootstrap.com/docs/5.2/utilities/sizing/)        |
| Spacing        | m-xx, p-xx               | [margin, padding](https://getbootstrap.com/docs/5.2/utilities/spacing/)       |
| Text           | text-xx,                 | [text 정렬 등등](https://getbootstrap.com/docs/5.2/utilities/text/)           |
| Vertical align | align-xx                 | [Vertical 정렬](https://getbootstrap.com/docs/5.2/utilities/vertical-align/)  |
| Visibility     | visible, invisible       | [보이고, 안보이고](https://getbootstrap.com/docs/5.2/utilities/visibility/)   |

# 8. Extend

- 확장에 대한 전략
  - 구축하고 유지 관리하는 데 사용되는 기본 원칙, 전략 및 기술
- Icons
  - > While Bootstrap doesn’t include an icon set by default, we do have our own comprehensive icon library called Bootstrap Icons.
  - [Font Awesome](https://fontawesome.com/)
  - [Feather](https://feathericons.com/)
  - [Octicons](https://primer.style/octicons/)
  - [More...](https://getbootstrap.com/docs/5.2/extend/icons/)

# 9. Apply Bootstrap

## 리스트 조회

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#21-list-ui)
  
- > IMPORTANT
  >> bootstrap css & javascript cdn 추가<br>
  >> 조회 조건 영역 변경(inline forms layout 반영)<br>
  >> table element 변경<br>
  >> 컨텐츠 중앙 정렬을 위하여 class="container" 추가<br>

```html
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
</head>

<body>
    <div class="container">
        <!-- 조회 조건 -->
        <div class="row row-cols-lg-auto g-3 align-items-center mt-1 mb-1">
            <div class="col-12">
                <select class="form-select" name="" id="gender">
                    <option value="">전체</option>
                    <option value="male">남자</option>
                    <option value="female">여자</option>
                </select>
            </div>

            <div class="col-12">
                <input type="search" class="form-control" name="" id="name" placeholder="Name" onkeyup="checkEnter()" />
            </div>

            <div class="col-12">
                <button class="btn btn-primary" onclick="doSearch();">조회</button>
                <button class="btn btn-success" onclick="goToCreate();">생성</button>
                <button class="btn btn-danger" id="btnDelete" onclick="doDelete();" disabled>삭제</button>
            </div>
        </div>

        <!-- 테이블 -->
        <table class="table table-striped table-hover">
            <thead>
                <tr>
                    <th><input type="checkbox" onchange="checkAll();" class="form-check-input" /></th>
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
    </div>



    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-kenU1KFdBIe4zVF0s0G1M5b4hcpxyD9F7jL+jjXkk+Q2h455rYXK/7HAuoJl+0I4"
        crossorigin="anonymous"></script>
    <script src="//cdn.jsdelivr.net/npm/sweetalert2@11"></script>
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
                h.push(
                    `<td><input type="checkbox" name="chk" value="${item.id}" onchange="isChecked();" class="form-check-input" /></td>`
                );
                h.push(
                    `<td><a href="javascript:goToDetail('${item.id}');">${item.name}</a></td>`
                );
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
            document.location.href = "dom_crud_create.html";
        }

        async function doDelete() {
            const chks = document.querySelectorAll("[name=chk]:checked");
            if (chks.length > 0) {
                Swal.fire({
                    title: "정말 삭제 하시겠습니까?",
                    text: "You won't be able to revert this!",
                    icon: "warning",
                    showCancelButton: true,
                    confirmButtonColor: "#3085d6",
                    cancelButtonColor: "#d33",
                    confirmButtonText: "삭제",
                    cancelButtonText: "취소",
                }).then(async (result) => {
                    if (result.isConfirmed) {
                        for (const chk of chks) {
                            await fetch(`http://localhost:3000/customers/${chk.value}`, {
                                method: "DELETE",
                            });
                        }

                        Swal.fire({
                            icon: "success",
                            title: "데이터가 정상적으로 삭제 되었습니다.",
                        });
                        await doSearch();
                    }
                });
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
            document.location.href = `dom_crud_detail.html?id=${id}&v1=1&name=jeremy`;
        }
    </script>
</body>
```

## 생성

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#22-create-ui)
  
- > IMPORTANT
  >> bootstrap css & javascript cdn 추가<br>
  >> 컨텐츠 중앙 정렬을 위하여 class="container" 추가<br>
  >> label, text, button 스타일 적용<br>
  >> alert 적용([sweetalert2](https://sweetalert2.github.io/))

```html
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
</head>

<body>
    <div class="container mt-2">
        <div class="row gy-2">
            <div class="col-4">
                <label for="name" class="form-label">Name</label>
            </div>
            <div class="col-8">
                <input type="text" name="" id="name" class="form-control" onkeyup="checkEnter('company')" />
            </div>
            <div class="col-4">
                <label for="name" class="form-label">Gender</label>
            </div>
            <div class="col-8">
                <input type="radio" name="gender" id="male" value="male" class="form-check-input" checked />
                <label for="male" class="form-check-label">남자</label>
                <input type="radio" name="gender" id="female" value="female" class="form-check-input" />
                <label for="female" class="form-check-label">여자</label>
            </div>
            <div class="col-4">
                <label for="company" class="form-label">Company</label>
            </div>
            <div class="col-8">
                <input type="text" name="" id="company" class="form-control" onkeyup="checkEnter('email')" />
            </div>
            <div class="col-4">
                <label for="email" class="form-label">Email</label>
            </div>
            <div class="col-8">
                <input type="email" name="" id="email" class="form-control" onblur="checkEmail();"
                    onkeyup="checkEnter('phone')" />
                <div id="emailMsg" class="invalid-feedback">
                    올바른 형식의 이메일을 입력하세요.
                </div>
            </div>
            <div class="col-4">
                <label for="phone" class="form-label">Phone</label>
            </div>
            <div class="col-8">
                <input type="tel" name="" id="phone" class="form-control" onblur="checkPhone();"
                    onkeyup="checkEnter('btnDaumAPI')" />
                <div id="phoneMsg" class="invalid-feedback">
                    올바른 형식의 전화번호를 입력하세요.
                </div>
            </div>
            <div class="col-4">
                <label for="address" class="form-label">Address</label>
            </div>
            <div class="col-8">
                <div class="input-group">
                    <button id="btnDaumAPI" onclick="openDaumAPI();" class="btn btn-dark">주소찾기</button>
                    <input type="text" name="" id="zonecode" class="form-control" readonly />
                </div>
                <input type="text" name="" id="address" class="form-control mt-1" class="form-control" readonly />
                <input type="text" name="" id="address2" class="form-control mt-1" placeholder="상세주소"
                    onkeyup="checkEnter('create')" />
            </div>
            <div class="text-center">
                <button onclick="doCreate();" class="btn btn-success">생성</button>
                <button onclick="goToList();" class="btn btn-secondary">목록</button>
            </div>
        </div>
    </div>


    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-kenU1KFdBIe4zVF0s0G1M5b4hcpxyD9F7jL+jjXkk+Q2h455rYXK/7HAuoJl+0I4"
        crossorigin="anonymous"></script>
    <script src="//cdn.jsdelivr.net/npm/sweetalert2@11"></script>
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
                return Swal.fire({
                    icon: 'info',
                    title: 'Name을 입력하세요.',
                    text: 'Name은 필수 입력값입니다.',
                })
            }

            if (company === "") {
                return alert("Company를 입력하세요.");
                return Swal.fire({
                    icon: 'info',
                    title: 'Company를 입력하세요.',
                    text: 'Company는 필수 입력값입니다.',
                })
            }

            const regexpEmail =
                /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
            if (!regexpEmail.test(email)) {
                return Swal.fire({
                    icon: "info",
                    title: "올바른 형식의 Email을 입력하세요.",
                    text: "이메일주소는 알파벳소문자, 숫자, 특수문자는 점(.)만 사용할 수 있습니다.",
                });
            }

            const regexpTel = /^010-\d{4}-\d{4}$/;
            if (!regexpTel.test(phone)) {
                return Swal.fire({
                    icon: "info",
                    title: "올바른 형식의 Phone을 입력하세요.",
                    text: "전화번호는 010-XXXX-XXXX 포맷으로 입력해야 합니다.",
                });
            }

            if (address === "") {
                return Swal.fire({
                    icon: "info",
                    title: "Address를 입력하세요.",
                    text: "Address는 필수 입력값입니다.",
                });
            }

            const zonecode = document.querySelector("#zonecode").value;
            const address2 = document.querySelector("#address2").value;

            Swal.fire({
                title: "정말 저장하시겠습니까?",
                text: "You won't be able to revert this!",
                icon: "warning",
                showCancelButton: true,
                confirmButtonColor: "#3085d6",
                cancelButtonColor: "#d33",
                confirmButtonText: "생성",
                cancelButtonText: "취소",
            }).then(async (result) => {
                if (result.isConfirmed) {
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
                        Swal.fire({
                            icon: "success",
                            title: "고객 정보가 정상적으로 생성되었습니다.",
                        });
                    } else {
                        Swal.fire({
                            icon: "error",
                            title: "고객 정보를 생성하지 못했습니다. 다시 시도하세요.",
                        });
                    }
                }
            });
        }

        function checkEmail() {
            const email = document.querySelector("#email").value;
            if (email !== "") {
                const regexpEmail =
                    /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
                if (!regexpEmail.test(email)) {
                    document.querySelector("#email").classList.add("is-invalid");
                    document.querySelector("#emailMsg").style.display = "block";
                } else {
                    document.querySelector("#email").classList.remove("is-invalid");
                    document.querySelector("#emailMsg").style.display = "none";
                }
            } else {
                document.querySelector("#email").classList.remove("is-invalid");
                document.querySelector("#emailMsg").style.display = "none";
            }
        }

        function checkPhone() {
            const phone = document.querySelector("#phone").value;
            if (phone !== "") {
                const regexpTel = /^010-\d{4}-\d{4}$/;
                if (!regexpTel.test(phone)) {
                    document.querySelector("#phone").classList.add("is-invalid");
                    document.querySelector("#phoneMsg").style.display = "block";
                } else {
                    document.querySelector("#phone").classList.remove("is-invalid");
                    document.querySelector("#phoneMsg").style.display = "none";
                }
            } else {
                document.querySelector("#phone").classList.remove("is-invalid");
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
            document.location.href = "dom_crud_list.html";
        }
    </script>
</body>
```

## 상세

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#23-detail-ui)
  
- > IMPORTANT
  >> bootstrap css & javascript cdn 추가<br>
  >> 컨텐츠 중앙 정렬을 위하여 class="container" 추가<br>
  >> label, text, button 스타일 적용<br>
  >> alert 적용([sweetalert2](https://sweetalert2.github.io/))

```html
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
</head>

<body>
    <div class="container mt-2">

        <div class="row mb-3">
            <label for="name" class="col-sm-3 col-form-label">Name</label>
            <div class="col-sm-9"><span id="name"></span></div>
        </div>

        <div class="row mb-3">
            <label for="name" class="col-sm-3 col-form-label">Gender</label>
            <div class="col-sm-9"><span id="gender"></span></div>
        </div>

        <div class="row mb-3">
            <label for="company" class="col-sm-3 col-form-label">Company</label>
            <div class="col-sm-9"><span id="company"></span></div>
        </div>

        <div class="row mb-3">
            <label for="email" class="col-sm-3 col-form-label">Email</label>
            <div class="col-sm-9"><span id="email"></span></div>
        </div>

        <div class="row mb-3">
            <label for="phone" class="col-sm-3 col-form-label">Phone</label>
            <div class="col-sm-9"><span id="phone"></span></div>
        </div>

        <div class="row mb-3">
            <label for="address" class="col-sm-3 col-form-label">Address</label>
            <div class="col-sm-9"><span id="address"></span></div>
        </div>

        <div class="text-center">
            <button onclick="goToUpdate();" class="btn btn-success">수정</button>
            <button onclick="goToList();" class="btn btn-secondary">목록</button>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-kenU1KFdBIe4zVF0s0G1M5b4hcpxyD9F7jL+jjXkk+Q2h455rYXK/7HAuoJl+0I4"
        crossorigin="anonymous"></script>
    <script src="./js/common.js"></script>
    <script>
        // queryString
        //   console.log(window.location.search);

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
            document.location.href = "dom_crud_list.html";
        }

        function goToUpdate() {
            const { id } = parseQueryString();
            document.location.href = `dom_crud_update.html?id=${id}`;
        }

        doSearchDetail();
    </script>
</body>
```

## 수정

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#24-update-ui)

- > IMPORTANT
  >> bootstrap css & javascript cdn 추가<br>
  >> 컨텐츠 중앙 정렬을 위하여 class="container" 추가<br>
  >> label, text, button 스타일 적용<br>
  >> alert 적용([sweetalert2](https://sweetalert2.github.io/))

```html
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
</head>

<body>
    <div class="container mt-2">
        <div class="row gy-2">
            <!-- name -->
            <div class="col-4">
                <label for="name" class="form-label">Name</label>
            </div>
            <div class="col-8">
                <input type="text" name="" id="name" class="form-control" onkeyup="checkEnter('company')" />
            </div>

            <!-- gender -->
            <div class="col-4">
                <label for="name" class="form-label">Gender</label>
            </div>
            <div class="col-8">
                <input type="radio" name="gender" id="male" value="male" class="form-check-input" checked />
                <label for="male" class="form-check-label">남자</label>
                <input type="radio" name="gender" id="female" value="female" class="form-check-input" />
                <label for="female" class="form-check-label">여자</label>
            </div>

            <!-- company -->
            <div class="col-4">
                <label for="company" class="form-label">Company</label>
            </div>
            <div class="col-8">
                <input type="text" name="" id="company" class="form-control" onkeyup="checkEnter('email')" />
            </div>

            <!-- email -->
            <div class="col-4">
                <label for="email" class="form-label">Email</label>
            </div>
            <div class="col-8">
                <input type="email" name="" id="email" class="form-control" onblur="checkEmail();"
                    onkeyup="checkEnter('phone')" />
                <div id="emailMsg" class="invalid-feedback">
                    올바른 형식의 이메일을 입력하세요.
                </div>
            </div>

            <!-- phone -->
            <div class="col-4">
                <label for="phone" class="form-label">Phone</label>
            </div>
            <div class="col-8">
                <input type="tel" name="" id="phone" class="form-control" onblur="checkPhone();"
                    onkeyup="checkEnter('btnDaumAPI')" />
                <div id="phoneMsg" class="invalid-feedback">
                    올바른 형식의 전화번호를 입력하세요.
                </div>
            </div>

            <!-- address -->
            <div class="col-4">
                <label for="address" class="form-label">Address</label>
            </div>
            <div class="col-8">
                <div class="input-group">
                    <button id="btnDaumAPI" onclick="openDaumAPI();" class="btn btn-dark">주소찾기</button>
                    <input type="text" name="" id="zonecode" class="form-control" readonly />
                </div>
                <input type="text" name="" id="address" class="form-control mt-1" readonly />
                <input type="text" name="" id="address2" class="form-control mt-1" placeholder="상세주소"
                    onkeyup="checkEnter('create')" />
            </div>

            <!-- button -->
            <div class="text-center">
                <button onclick="doSave();" class="btn btn-success">저장</button>
                <button onclick="goToList();" class="btn btn-secondary">목록</button>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-kenU1KFdBIe4zVF0s0G1M5b4hcpxyD9F7jL+jjXkk+Q2h455rYXK/7HAuoJl+0I4"
        crossorigin="anonymous"></script>
    <script src="//cdn.jsdelivr.net/npm/sweetalert2@11"></script>
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
                return Swal.fire({
                    icon: "info",
                    title: "Name을 입력하세요.",
                    text: "Name은 필수 입력값입니다.",
                });
            }

            if (company === "") {
                return Swal.fire({
                    icon: "info",
                    title: "Company를 입력하세요.",
                    text: "Company는 필수 입력값입니다.",
                });
            }

            const regexpEmail =
                /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
            if (!regexpEmail.test(email)) {
                return Swal.fire({
                    icon: "info",
                    title: "올바른 형식의 Email을 입력하세요.",
                    text: "이메일주소는 알파벳소문자, 숫자, 특수문자는 점(.)만 사용할 수 있습니다.",
                });
            }

            const regexpTel = /^010-\d{4}-\d{4}$/;
            if (!regexpTel.test(phone)) {
                return Swal.fire({
                    icon: "info",
                    title: "올바른 형식의 Phone을 입력하세요.",
                    text: "전화번호는 010-XXXX-XXXX 포맷으로 입력해야 합니다.",
                });
            }

            if (address === "") {
                return Swal.fire({
                    icon: "info",
                    title: "Address를 입력하세요.",
                    text: "Address는 필수 입력값입니다.",
                });
            }

            const zonecode = document.querySelector("#zonecode").value;
            const address2 = document.querySelector("#address2").value;

            const { id } = parseQueryString();

            Swal.fire({
                title: "정말 저장하시겠습니까?",
                text: "You won't be able to revert this!",
                icon: "warning",
                showCancelButton: true,
                confirmButtonColor: "#3085d6",
                cancelButtonColor: "#d33",
                confirmButtonText: "생성",
                cancelButtonText: "취소",
            }).then(async (result) => {
                if (result.isConfirmed) {
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
                        Swal.fire({
                            icon: "success",
                            title: "정상적으로 저장되었습니다.",
                        });
                    } else {
                        Swal.fire({
                            icon: "error",
                            title: "고객 정보를 저장하지 못했습니다. 다시 시도하세요.",
                        });
                    }
                }
            });
        }

        function checkEmail() {
            const email = document.querySelector("#email").value;
            if (email !== "") {
                const regexpEmail =
                    /^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
                if (!regexpEmail.test(email)) {
                    document.querySelector("#email").classList.add("is-invalid");
                    document.querySelector("#emailMsg").style.display = "block";
                } else {
                    document.querySelector("#email").classList.remove("is-invalid");
                    document.querySelector("#emailMsg").style.display = "none";
                }
            } else {
                document.querySelector("#email").classList.remove("is-invalid");
                document.querySelector("#emailMsg").style.display = "none";
            }
        }

        function checkPhone() {
            const phone = document.querySelector("#phone").value;
            if (phone !== "") {
                const regexpTel = /^010-\d{4}-\d{4}$/;
                if (!regexpTel.test(phone)) {
                    document.querySelector("#phone").classList.add("is-invalid");
                    document.querySelector("#phoneMsg").style.display = "block";
                } else {
                    document.querySelector("#phone").classList.remove("is-invalid");
                    document.querySelector("#phoneMsg").style.display = "none";
                }
            } else {
                document.querySelector("#phone").classList.remove("is-invalid");
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
            document.location.href = "dom_crud_list.html";
        }
    </script>
</body>
```

## 삭제

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#21-list-ui)
  
- > IMPORTANT
  >> alert 적용([sweetalert2](https://sweetalert2.github.io/))
  >> `doDelete()` function에서 `sweetalert2` 적용

```javascript
<script src="//cdn.jsdelivr.net/npm/sweetalert2@11"></script>

async function doDelete() {
    const chks = document.querySelectorAll("[name=chk]:checked");
    if (chks.length > 0) {
        Swal.fire({
            title: "정말 삭제 하시겠습니까?",
            text: "You won't be able to revert this!",
            icon: "warning",
            showCancelButton: true,
            confirmButtonColor: "#3085d6",
            cancelButtonColor: "#d33",
            confirmButtonText: "삭제",
            cancelButtonText: "취소",
        }).then(async (result) => {
            if (result.isConfirmed) {
                for (const chk of chks) {
                    await fetch(`http://localhost:3000/customers/${chk.value}`, {
                        method: "DELETE",
                    });
                }

                Swal.fire({
                    icon: "success",
                    title: "데이터가 정상적으로 삭제 되었습니다.",
                });
                await doSearch();
            }
        });
    } else {
        alert("삭제할 아이템을 선택하세요.");
    }
}
```

## 멀티생성

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#25-multiple-create-ui)
  
- > IMPORTANT
  >> bootstrap css & javascript cdn 추가<br>
  >> 컨텐츠 중앙 정렬을 위하여 class="container" 추가<br>
  >> label, text, button 스타일 적용<br>
  >> 저장시 유효성 검사 및 알람창 표시<br>
  >> alert 적용([sweetalert2](https://sweetalert2.github.io/))

```html
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
</head>

<body>
    <div class="container">
        <!-- 조회 조건 -->
        <div class="mb-2 mt-3">
            <button id="btnSave" onclick="doSave();" class="btn btn-success" disabled>
                저장
            </button>
            <button onclick="addLine();" class="btn btn-dark">라인추가</button>
            <button id="btnRemove" onclick="removeLine();" class="btn btn-danger" disabled>
                라인삭제
            </button>
        </div>

        <!-- 테이블 -->
        <table class="table table-striped table-hover">
            <thead>
                <tr>
                    <th><input type="checkbox" onchange="checkAll();" class="form-check-input" /></th>
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
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-kenU1KFdBIe4zVF0s0G1M5b4hcpxyD9F7jL+jjXkk+Q2h455rYXK/7HAuoJl+0I4"
        crossorigin="anonymous"></script>
    <script src="//cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script>
        function addLine() {
            const h = [];
            h.push(`<tr>`);
            h.push(`<td><input type="checkbox" name="chk" onchange="isChecked();" class="form-check-input" /></td>`);
            h.push(`<td><input type="text" name="name" class="form-control" /></td>`);
            h.push(`<td><input type="text" name="company" class="form-control" /></td>`);
            h.push(`<td><select name="gender" class="form-select"><option value="male" selected>남자</option><option value="female">여자</option></select></td>`);
            h.push(`<td><input type="text" name="email" class="form-control" /></td>`);
            h.push(`<td><input type="text" name="phone" class="form-control" /></td>`);
            h.push(`<td><input type="text" name="address" class="form-control" /></td>`);
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

                        if (name === "" || company === "" || email === "" || phone === "" || address === "") {
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
                    //return alert(`${blankRows.join(",")}행에 비어 있는 값이 존재합니다. 모든 값을 입력하세요.`);
                    return Swal.fire({
                        icon: "info",
                        title: "필수값 입력 체크",
                        text: `${blankRows.join(",")}행에 비어 있는 값이 존재합니다. 모든 값을 입력하세요.`,
                    });
                }

                if (!passEmail) {
                    //return alert(`${wrongEmails.join(",")}행에 입력한 이메일 형식이 올바르지 않습니다.`);
                    return Swal.fire({
                        icon: "info",
                        title: "이메일 형식 체크",
                        text: `${wrongEmails.join(",")}행에 입력한 이메일 형식이 올바르지 않습니다.`,
                    });
                }

                if (!passPhone) {
                    //return alert(`${wrongPhones.join(",")}행에 입력한 전화번호 형식이 올바르지 않습니다.`);
                    return Swal.fire({
                        icon: "info",
                        title: "전화번호 형식 체크",
                        text: `${wrongPhones.join(",")}행에 입력한 전화번호 형식이 올바르지 않습니다.`,
                    });
                }

                const failData = [];
                Swal.fire({
                    title: "정말 저장하시겠습니까?",
                    text: "You won't be able to revert this!",
                    icon: "warning",
                    showCancelButton: true,
                    confirmButtonColor: "#3085d6",
                    cancelButtonColor: "#d33",
                    confirmButtonText: "생성",
                    cancelButtonText: "취소",
                }).then(async (result) => {
                    if (result.isConfirmed) {
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
                            Swal.fire({
                                icon: "error",
                                title: `저장에 실패한 데이터가 ${failData.length}건 있습니다.`,
                            });
                        } else {
                            Swal.fire({
                                icon: "success",
                                title: "정상적으로 저장 되었습니다.",
                            });
                        }
                    }
                });
            }
        }
    </script>
</body>
```

# 10. Theme

# 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)