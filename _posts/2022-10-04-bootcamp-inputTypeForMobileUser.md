---
title:  "[BootCamp 5기] - Input Type for Mobile User"
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, html, input type]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-04
last_modified_at: 2022-10-05
---

[<img src="https://i0.wp.com/css-tricks.com/wp-content/uploads/2020/04/qyjE-kzw.png?resize=1000%2C822&ssl=1" width="100%"/>](<img src="https://i0.wp.com/css-tricks.com/wp-content/uploads/2020/04/qyjE-kzw.png?resize=1000%2C822&ssl=1" width="100%"/>)

## 1. Input Type for Mobile User

- 모바일 장치에서 앱의 성능을 향상시키는 간단하고 실용적인 방법은 항상 **올바른 유형(Correct Type)**, **입력 모드(Input Mode)** 및 **자동 완성(Auto Complete)** *속성*으로 HTML Input Fields를 구성하는 것이다. 이 세 가지 속성은 개별적으로 보다 함께 고려됨으로 모바일 사용자에게 좋은 사용자 경험을 제공 한다.
- 

### 1.1 올바른 유형(Correct Type)

- 올바른 타입을 통하여 모바일 사용자에게 효과적인 입력(선택)의 경험을 제공
- [email](https://better-mobile-inputs.netlify.app/?android=false&autocomplete&inputmode&type=email), [telephone number](https://better-mobile-inputs.netlify.app/?android=false&autocomplete&inputmode&type=tel) ...

### 1.2 입력 모드(Input Mode)

- Input Mode 속성을 사용하면 모바일 키보드를 재정의하여 사용자에게 표시됨으로 키보드의 유형을 직접 지정 및 선언 할 수 있음.

```html
<input type="number"/>

<input type="Text" inputmode="decimal"/>
```

- iOS left : numeric / iOS right : decimal
<img src="https://i0.wp.com/css-tricks.com/wp-content/uploads/2020/04/input-numeric-ios.png?resize=1000%2C414&ssl=1" width="80%"/>

### 1.3 자동 완성(Auto Complete)

- 자동 완성 제안을 표시함으로 모바일에서 더 빠르고 덜 답답한 사용자 경험을 만들 수 있다.
- [HTML attribute:autocomplete](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete)

### 1.4 날짜 타입(Date Type)

- 날짜, 시간, 로컬 날짜/시간, 달력과 같이 세밀한 날짜 타입을 제공
- [Date Type](https://better-mobile-inputs.netlify.app/?android=false&autocomplete&inputmode&type=date), [Time Type](https://better-mobile-inputs.netlify.app/?android=false&autocomplete&inputmode&type=time) ...

## 2. Reference

### 2.1 [Better Form Inputs for Better Mobile User Experiences](https://css-tricks.com/better-form-inputs-for-better-mobile-user-experiences/)