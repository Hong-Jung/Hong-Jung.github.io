---
title:  "CSS Box Model 이란 ?"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, BoxModel]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-23
last_modified_at: 2022-10-23
---

# WHAT IS ***BoxModel*** IN CSS ???

## 1. Index

- [WHAT IS ***BoxModel*** IN CSS ???](#what-is-boxmodel-in-css-)
  - [1. Index](#1-index)
  - [2. Introduction](#2-introduction)
  - [3. Body](#3-body)
    - [1. BoxModel 구성 요소](#1-boxmodel-구성-요소)
      - [1.1 박스 내 콘텐츠 흐름을 제어하는 속성](#11-박스-내-콘텐츠-흐름을-제어하는-속성)
      - [1.2 박스 크기를 제어하는 속성](#12-박스-크기를-제어하는-속성)
      - [1.3 박스의 바깥 여백을 제어하는 속성](#13-박스의-바깥-여백을-제어하는-속성)
      - [1.4 박스의 안쪽 여백을 제어하는 속성](#14-박스의-안쪽-여백을-제어하는-속성)
      - [1.5 기타 속성](#15-기타-속성)
    - [2. box-sizing](#2-box-sizing)
      - [2.1 구문, 형식 구분](#21-구문-형식-구분)
      - [2.2 예제](#22-예제)
  - [4. Conclusion](#4-conclusion)
  - [5. Reference](#5-reference)

## 2. Introduction 

- A box in CSS consists of a content area, which is where any text, images, or other HTML elements are displayed. This is optionally surrounded by padding, a border, and a margin, on one or more sides. The box model describes how these elements work together to create a box as displayed by CSS.
- CSS의 상자는 텍스트, 이미지 또는 기타 HTML 요소가 표시되는 콘텐츠 영역으로 구성됩니다. 이것은 선택적으로 하나 이상의 면에서 패딩, 테두리 및 여백으로 둘러싸여 있습니다. 상자 모델은 이러한 요소가 함께 작동하여 CSS에 표시되는 상자를 만드는 방법을 설명합니다.

## 3. Body

### 1. BoxModel 구성 요소 

- 문서의 레이아웃을 계산할 때, 브라우저의 렌더링 엔진은 표준 CSS 기본 박스 모델에 따라 각각의 요소를 사각형 박스로 표현합니다. CSS는 박스의 크기, 위치, 속성(색, 배경, 테두리 모양 등)을 결정합니다.
- 하나의 박스는 네 부분(영역)으로 이루어집니다. 각 영역을 콘텐츠 영역, 안쪽 여백(패딩) 영역, 테두리 영역, 그리고 바깥 여백(마진) 영역이라고 부릅니다.
- [박스 모델 기본](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
  - Content area
  - Padding area
  - Border area
  - Margin area

#### 1.1 박스 내 콘텐츠 흐름을 제어하는 속성

- overflow
- overflow-x (en-US)
- overflow-y (en-US)

#### 1.2 박스 크기를 제어하는 속성

- height
- width
- max-height
- max-width
- min-height
- min-width

#### 1.3 박스의 바깥 여백을 제어하는 속성

- margin
- margin-bottom
- margin-left
- margin-right
- margin-top
- margin-trim (en-US) Experimental

#### 1.4 박스의 안쪽 여백을 제어하는 속성

- padding
- padding-bottom
- padding-left
- padding-right
- padding-top

#### 1.5 기타 속성

- visibility
  
### 2. box-sizing

- [box-sizing CSS 속성은 요소의 너비와 높이를 계산하는 방법을 지정합니다.](https://developer.mozilla.org/ko/docs/Web/CSS/box-sizing)

#### 2.1 구문, 형식 구분

- 5

#### 2.2 예제

- 6

## 4. Conclusion

- 1

## 5. Reference

- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)