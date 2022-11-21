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

- [1. What is bootstrap ?](#1-what-is-bootstrap-)
- [2. Layout](#2-layout)
- [3. Content](#3-content)
- [4. Forms](#4-forms)
- [5. Components](#5-components)
- [6. Helpers](#6-helpers)
- [7. Utilities](#7-utilities)
- [8. Extend](#8-extend)
- [9. Apply Bootstrap](#9-apply-bootstrap)
  - [리스트 조회](#리스트-조회)
  - [생성](#생성)
  - [상세](#상세)
  - [삭제](#삭제)
  - [멀티생성](#멀티생성)
- [10. Theme](#10-theme)
- [참고](#참고)

# 1. What is bootstrap ?

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
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>

## 생성

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#22-create-ui)
  
- > IMPORTANT
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>

## 상세

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#23-detail-ui)
  
- > IMPORTANT
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>

## 삭제

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#24-update-ui)
  
- > IMPORTANT
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>

## 멀티생성

- 주요 변경 사항
  - [기존의 소트 코드](https://hong-jung.github.io/bootcamp/bootcamp-javascript-dom_crud/#25-multiple-create-ui)
  
- > IMPORTANT
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>
  >> sssss<br>

# 10. Theme

# 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)