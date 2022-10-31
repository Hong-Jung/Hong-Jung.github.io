---
title:  "[Blog] What is Image Map Tag ???"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, map tag]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-11
last_modified_at: 2022-10-11
---

# WHAT IS ***IMAGE MAP*** TAG ???

## 1. Index

- [WHAT IS ***IMAGE MAP*** TAG ???](#what-is-image-map-tag-)
  - [1. Index](#1-index)
  - [2. Introduction](#2-introduction)
  - [3. Body](#3-body)
    - [1. IKEA 홈페이지의 이미지 맵에 대한 분석](#1-ikea-홈페이지의-이미지-맵에-대한-분석)
      - [1.1 기능 위주의 분석](#11-기능-위주의-분석)
      - [1.2 코드 위주의 분석](#12-코드-위주의-분석)
    - [2. 이미지 맵 태그 생성 도구 및 태그 자동 생성](#2-이미지-맵-태그-생성-도구-및-태그-자동-생성)
      - [2.1 태그 자동 생성 도구란?](#21-태그-자동-생성-도구란)
      - [2.2 이미지 준비](#22-이미지-준비)
      - [2.3 자동 생성 도구 종류 및 사용법](#23-자동-생성-도구-종류-및-사용법)
    - [3. 웹페이지 적용](#3-웹페이지-적용)
  - [4. Conclusion](#4-conclusion)
  - [5. Reference](#5-reference)

----

## 2. Introduction 

- Image Map Tag란 무엇일까?
  - 이미지의 특정 좌표(x축, y축)를 기준으로 링크 정보를 생성하여 페이지 이동(효과)이 가능하다. 다국적 기업인 IKEA의 홈페이지에서 많은 사례를 찾아 볼 수 있다. 

  > "HTML 3.2 버전에서 서버에서의 이미지맵 처리를 대체하기 위해서 도입되었다고 한다. 기존의 서버측 이미지 맵을 클릭한 좌료를 기반으로 어디로 링크가 이동할지 클라이언트와 서버간 통신이 이루어져야 했음으로 투박(?)했다고 하지만, 사용해 보지 않은 관계로 문구만 빌려 표기 했다. 이를 보완하기 위해서 클라이언트 측 이미지 맵이 탄생 했다고 한다.!
  >
  >> 그리하여 이미지맵의 기능 요건은 사용자가 이미지의 특정 부분을  클릭하고 다른 목적지(링크등)로 이동할 수 있는 그래픽 이미지이다. 이미지 맵은 x 및 y 좌표(왼쪽 상단 모서리 기준)로 구성되며, 각 좌표 세트(x축, y축)를 사용하여 사용자가 영역 내를 클릭할 때 이동할 링크를 지정한다.
  >
  > 예를 들어 이미지 지도로 사용하려는 세계 지도가 있다고 가정해 보자. 각 국가는 다른 페이지로 이동하기 위해 지도에 정의된 핫 영역(좌표 세트)을 가질 수 있다.
  > 
  > [Image map 인용구](https://www.image-map.net/)
  
<!-- [<img src="../../assets/images/posts/bootcamp005/image_map_sample_ikea.png" width="300px" alt="IKEA 샘플 이미지" align="center"/>](https://www.ikea.com/kr/ko/?ref=gwp-start) -->

[<img src="../../assets/images/posts/bootcamp005/image_map_sample_ikea.png" width="300px" align="center"/>](https://www.ikea.com/kr/ko/?ref=gwp-start)

- 자, 이미지 맵이 무엇인지 어디에 적용할 수 있는지 살펴 보았다. 
  이제 실전이다. 하나하나 따라서 진행해 보자.

## 3. Body

### 1. IKEA 홈페이지의 이미지 맵에 대한 분석   

- 아래의 이미지를 보면 실제 이미지에 3개의 영역을 구분하여, 각 영역에 `Hover or Click`시 이벤트 처리를 통하여 추가 정보를 표시하고 있다.
  - A : 배경 이미지 영역
  - B : 3개의 상세 영역을 구분하고 각 영역의 `<a>` 태그 또는 추가 정보를 위한 `<div>` 태크 사용
- <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis.png" width="100%"/>
- 태그(코드)의 양도 많으며, 가독성도 떨어진다. 아마 다른 툴을 활용해서 상세 코드를 생성하지 않았을까? 라는 생각을 해 본다.

#### 1.1 기능 위주의 분석

- B 영역에 대해서 간단하게 분석해 보자
- *둥근 영역*에 마우스를 `Hover`하면 우측으로 `<div>` 태그를 활용하여 *간략한 정보*를 표시 한다.
- *둥근 영역*이나 *간략 정보 영역*을 `click`하면 `<a>` 태그를 이용하여 *상세 페이지로 이동* 한다.
- <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis_2.png" width="100%"/>

#### 1.2 코드 위주의 분석

- 굳지 분석할 필요가 있을까? 너무 복잡하다. 분석하고 싶은 의욕이 떨어진다. :(
- 위의 *크롬 개발자 도구*에서 캡쳐한 이미지를 참고해서 코드의 양만 봐도 공감하리라 생각한다.

### 2. 이미지 맵 태그 생성 도구 및 태그 자동 생성

- 이미지 파일을 기반으로 내부에 영역을 표시(구분)해 주는 도구들이 많이 존재한다.
- 이를 활용하면 손 쉽게 이미지 맵 태그를 생성할 수 있다.

#### 2.1 태그 자동 생성 도구란?

- 무료로 HTML 기반 이미지 맵을 매우 쉽게 만들 수 있으며, 최신 브라우저(브라우저 지원 여부 확인 필요)를 지원 한다.
- 클라이언트 측에서만 동작하며(서버측으로 데이터 발송하지 않음), HTML5, SVG 및 JavaScript의 장점을 사용한다.

- `<map>` 태그는 클라이언트 측 이미지 맵을 정의하는 데 사용되며, 이미지 맵은 클릭 가능한 영역이 있는 이미지이다.
- `<map>` 요소의 필수 속성은 `<img>`의 `usemap` 속성과 연결되며, 이미지와 지도 간의 관계를 생성한다.
- `<map>` 요소에는 이미지 맵에서 클릭 가능한 영역을 정의하는 다수의 `<area>` 요소가 포함된다.
- 태그 생성 싸이트를 이용하면 이미지맵을 위한 태그를 아주 손쉽게 만들 수 있다.

#### 2.2 이미지 준비

- 아래와 같이 이미지에 맵을 적용할 이미지를 검색하여 확보 한다.
- 본인의 경우 파워포인트를 사용하여 미리 맵 영역을 표시 하였다.
- <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis_3.png"/>

#### 2.3 자동 생성 도구 종류 및 사용법

- [Image-Map](https://www.image-map.net/)
  - *Image-Map* 이라는 이름의 싸이트이며, 로컬 이미지를 바로 오픈하여 맵 영역을 표시하고 링크등의 속성을 적용한 *tag*를 확보 할 수 있다.
  - 사용법은 다음과 같다.
  - <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis_4.png"/>
  - A : `Select Image from My PC`를 클릭하여 맵을 만들 이미지 파일을 로딩한다.
  - B : `C영역`의 *area*를 선택하고 상단 이미지에 맵 영역을 만들 부위를 `클릭`하여 영역 지정
  - C : Shape(원, 사각형, 다각형), Link, Title, Target 속성을 지정
  - D : area 추가
  - E : Tag 자동 생성을 위하여 `Show Me The Code!` 클릭
  - F : 자동으로 생성된 *Image map tag*.
- [imagemap](https://imagemap.org/)
  - *imagemap.org*이라는 이름의 싸이트이며, 동일하게 로컬 이미지를 바로 오픈하여 맵 영역을 표시하고 링크들의 속성을 적용한 *tag*를 확보 할 수 있다.
  - 사용법은 다음과 같다.
  - <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis_5.png"/>
  - A : `SELECT IMAGE`를 클릭하여 맵을 만들 이미지 파일을 로딩한다.
  - B : `area`의 형태를 *사각형, 원, 다각형* 중 선택할 수 있다. (C에서 지우고 싶은 area 선택 후 *삭제*도 가능)
  - C : *Link, Title* 속성을 입력, 수정할 수 있는 속성 영역
  - D : 자동으로 생성된 *Image map tag*.

### 3. 웹페이지 적용

- 간단하게 image map을 적용해 보자.
- 적용할 html 파일의 내용이다.

- ```html
  <img src="./img/그림1.png" usemap="#image-map">

  <map name="image-map">
    <area target="_blank" alt="google" title="google" href="https://www.google.com" coords="533,341,20" shape="circle">
    <area target="_blank" alt="naver" title="naver" href="https://www.naver.com" coords="1191,511,20" shape="circle">
  </map>
  ```

- 실제 적용 화면(Sample)
- <img src="../../assets/images/posts/bootcamp005/ikea_image_link_analysis_6.png"/>

## 4. Conclusion

- `img` 요소의 `usemap` 속성 ***value***와 `map` 요소의 `name` 속성 ***value***와 일치화 시킴으로써 이미지의 좌표를 이용하기 용이하다는 점이 상당히 매리트 있어 보인다. 링크 속성에서 더 확장해 container 요소를 사용하여 다양한 정보를 표현하다면 좋은 **UX**를 제공하리라 생각 한다.

## 5. Reference

- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)
- [Image-Map](https://www.image-map.net/)
- [imagemap](https://imagemap.org/)