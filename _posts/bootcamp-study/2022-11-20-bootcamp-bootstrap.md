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

# Bootstrap

- [Bootstrap](#bootstrap)
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

## 1. What is bootstrap ?

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

## 2. Layout

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

## 3. Content

- Reboot, Typography, Images, Tables, Figures가 있다.
- Typography([bootstrap typography](https://getbootstrap.com/docs/5.2/content/typography/))
  - 글자 관련된 디자인 클래스들 제공
- Images([bootstrap images](https://getbootstrap.com/docs/5.2/content/images/))
  - 이미지 관련된 디자인 클래스 제공
  - `class='img-fluid'`는 반응형 이미지 사용(가장 많이 사용)
- Tables([bootstrap tables](https://getbootstrap.com/docs/5.2/content/tables/))
  - 테이블(table) 태그(tag)에 대한 디자인 클래스 제공

  - ```html
    <table class="table table-secondary table-striped table-hover table-bordered">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Mark</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Jacob</td>
          <td>Thornton</td>
          <td>@fat</td>
        </tr>
        <tr>
          <th scope="row">3</th>
          <td colspan="2">Larry the Bird</td>
          <td>@twitter</td>
        </tr>
      </tbody>
    </table>
    ```

## 4. Forms

## 5. Components

## 6. Helpers

## 7. Utilities

## 8. Extend

## 9. Apply Bootstrap

### 리스트 조회

### 생성

### 상세

### 삭제

### 멀티생성

## 10. Theme

## 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)