---
title:  "Vue Advanced"
excerpt: "개발자의품격"
comments: true
header:

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, Vue]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-12-01
last_modified_at: 2022-12-01
---

- [1. Vuejs Advanced](#1-vuejs-advanced)
- [2. Custom Directive](#2-custom-directive)
- [3. Mixins](#3-mixins)
- [4. Plugin](#4-plugin)
- [5. Vuex](#5-vuex)
- [6. Composition API](#6-composition-api)
- [7. Kakao Login API](#7-kakao-login-api)
- [8. Naver Login API](#8-naver-login-api)
- [9. Daum Post Number API](#9-daum-post-number-api)
- [10. Kakao Map API](#10-kakao-map-api)
- [11. 참고](#11-참고)

# 1. Vuejs Advanced

<img src="https://www.vectorlogo.zone/logos/vuejs/vuejs-ar21.svg" width="100%" align="center"/>

- [Vuejs 공식 사이트](https://vuejs.org/)

# 2. Custom Directive

- v-on, v-bind와 같은 키워드를 directive라고 부르며, 이러한 directive를 custom하게 구현할 수 있음

> **IMPORTANT**
>> Directive를 Custom하게 구현 가능 `v-` prefix 사용
>>
>> - `v-xxx` 같이 단순 directive, `v-xxx="값"` 같이 직접 값 할당 directive, `v-xxx="{id:1, name:'john'}"` 같이 바인딩 방법
>> - `directives: {}` 내부에 `모든 Life Cycle Hook` 요소를 사용하여 구현
>> - Life Cycle Hook 요소의 구현 함수에 `인자 값으로 el, binding` 사용 가능
>> - Global하게 사용 가능(main.js에 구현하며 내부/외부 코드로 가능)

- custom directive
  - v-focus와 같이 그냥 directive 키워드만 사용 방법
  - v-focus directive에 바로 값 할당 = "color" 방법
  - v-focus="{color:'red',text='hello!'}와 같이 바인딩 방법

- 소문자만, 대문자만, 숫자만, 한국어만 등등 공통으로 사용 가능
  - 전역 사용을 위한 설정은 main.js에 다음과 같이 선언
    - app.mount() 전에만 하면 됨
    - app.directive(....)
    - 외부 파일로 빼서 작성할 수 도 있음
  
```html
directives: {
  focus: {
    life cycle hoot 모두 가능(el, binding) {}
  }
}
```

# 3. Mixins

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 4. Plugin

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 5. Vuex

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 6. Composition API

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 7. Kakao Login API

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 8. Naver Login API

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 9. Daum Post Number API

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 10. Kakao Map API

- Contents

> **IMPORTANT**
>> Vue.js
>>
>> - contents
>> - contents

```html
```

# 11. 참고

- [개발자의 품격 youtube](https://www.youtube.com/c/%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%9D%98%ED%92%88%EA%B2%A9)
- [MDN Site](https://developer.mozilla.org/ko/)
- [W3C Site](https://www.w3.org/)
- [Can I use ? Site](https://caniuse.com/)