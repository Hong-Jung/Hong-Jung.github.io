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
  
```html
<template>
  <div>
    <div>
      <label for="email" class="form-label">이메일주소</label>
      <input type="email" name="" id="email" class="form-control" v-focus />
    </div>
  </div>

  <div v-color="color" style="height: 50px"></div>
  <div v-demo="{ color: 'red', text: 'hello!' }"></div>
  <div>
    <input type="text" name="" id="" v-lowercase class="form-control" />
  </div>
  <div>
    <input type="text" name="" id="" v-uppercase class="form-control" />
  </div>
  <div>
    <input type="text" name="" id="" v-number class="form-control" />
    <input type="number" name="" id="" class="form-control" />
  </div>
  <div>
    <input type="text" name="" id="" v-korean class="form-control" />
  </div>
</template>
<script>
export default {
  components: {},
  directives: {
    focus: {
      mounted(el, binding) {
        console.log(el)
        el.focus()
      }
    },
    lowercase: {
      mounted(el) {
        el.addEventListener('input', (event) => {
          console.log(event.target.value)
          event.target.value = event.target.value.toLowerCase()
        })
      }
    },
    uppercase: {
      mounted(el) {
        el.addEventListener('input', (event) => {
          console.log(event.target.value)
          event.target.value = event.target.value.toUpperCase()
        })
      }
    },
    number: {
      mounted(el) {
        el.addEventListener('input', (event) => {
          console.log(event.target.value)
          event.target.value = event.target.value.replace(/\D/g, '')
        })
      }
    },
    korean: {
      mounted(el) {
        el.addEventListener('input', (event) => {
          console.log(event.target.value)
          event.target.value = event.target.value.replace(/[^ㄱ-ㅎ|ㅏ-ㅣ|가-힣]/g, '')
        })
      }
    },
    color: {
      mounted(el, binding) {
        console.log(binding.value)
        el.style.backgroundColor = binding.value
      }
    },
    demo: {
      mounted(el, binding) {
        el.innerText = binding.value.text
        el.style.color = binding.value.color
      }
    }
  }
}
</script>
```

> **IMPORTANT**
>> 전역 사용을 위한 설정은 main.js에 다음과 같이 선언
>>
>> - `app.mount() 전`에 정의
>> - `app.directive(....)` 형식으로 구현
>> - `외부 파일`로 작성하여 사용 가능
>> - 각 파일에서는 전역으로 선언한 Directive 키워드 `v-focus`, `v-lowercase` 사용

```javascript
<!-- main.js에 mount() 전 directive()로 정의 -->
app.directive('focus', {
  mounted(el, binding) {
    el.focus()
  }
})

app.directive('lowercase', {
  mounted(el) {
    el.addEventListener('input', (event) => {
      event.target.value = event.target.value.toLowerCase()
    })
  }
})
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