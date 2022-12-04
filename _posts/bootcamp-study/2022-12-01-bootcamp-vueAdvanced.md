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
- custom하게 만든 directive를 life cycle hook을 이용하여 사용 가능

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

- Vue Component의 코드와 Javascript 코드를 섞어 하개의 파일과 같이 사용할 수 있다.

> **IMPORTANT**
>> Mixin
>>
>> - 여러개의 콤포넌트 간의 공통으로 사용되는 코드(로직)를 재사용할 수 있는 방법
>> - 통상적으로 mixin 함수는 `"$" prefix`를 사용한다.
>> - `mixin 의 함수부터 먼저 수행` 된다.(라이프 사이클 훅 메서드를 기준으로)
>> - custom derective와 동일하게 `Global(main.js)에 등록하여 전역으로 사용`할 수 있다.
>> - import 할때 from 키워드에서 `index.js` 파일은 기본 파일로 제외해도 된다.
>> - `$route.path` 함수를 사용하여 component 접속 로그 기록 가능

```html
<!-- mixin을 사용할 vue component -->
<template>
  <div></div>
</template>
<script>
import Formater from '@/mixins/formatter.js'

export default {
  mixins: [Formater],
  created() {
    console.log('MixinView의 created')
  },
  mounted() {
    console.log('MixinView의 mounted')
    console.log(this.$convertDateFormat('20220601', 'YYYY-MM-DD'))
    console.log(this.$convertDateFormat('20220601', 'MM.DD.YYYY'))
  }
}
</script>

<script>
// formatter.js : mixin 시킬 코드
export default {
  created() {
    console.log('formatter의 created')
  },
  mounted() {
    console.log('formatter의 mounted')
  },
  unmounted() {},
  methods: {
    $convertDateFormat(d, f) {
      let year = ''
      let month = ''
      let day = ''

      // '20221201'
      // Date
      if (typeof d === 'string' && d.length === 8) {
        year = d.substr(0, 4)
        month = d.substr(4, 2)
        day = d.substr(6, 2)
      } else if (typeof d === 'object') {
        year = d.getFullYear()
        month = (d.getMonth() + 1).toString().padStart(2, 0)
        day = (d.getDate() + 1).toString().padStart(2, 0)
      }

      // f - 'YYYY-MM-DD', 'MM-DD-YYYY'
      return f.replace('YYYY', year).replace('MM', month).replace('DD', day)
    }
  }
}
</script>
```

> **IMPORTANT**
>> [Axios 공식 사이트](https://axios-http.com/kr/docs/intro)
>>
>> - 브라우저와 node.js에서 사용할 수 있는 Promise 기반 HTTP 클라이언트 라이브러리
>> - main.js에 Global 사용을 위하여 등록하여 사용할 수 있다.

```javascript
import axios from 'axios'

axios.defaults.baseURL = 'http://localhost:3000'
axios.defaults.headers['Content-Type'] = 'application/json;charset=utf-8'
axios.defaults.headers['Access-Control-Allow-Origin'] = '*'

export default {
  methods: {
    async $get(url) {
      return (
        await axios.get(url).catch((e) => {
          console.log(e)
        })
      ).data
    },
    async $post(url, data) {
      return await axios.post(url, data).catch((e) => {
        console.log(e)
      })
    },
    async $put(url, data) {
      return await axios.put(url, data).catch((e) => {
        console.log(e)
      })
    },
    async $delete(url) {
      return await axios.delete(url).catch((e) => {
        console.log(e)
      })
    }
  }
}
```

# 4. Plugin

- Contents

> **IMPORTANT**
>> [Vuejs Plugin 공식 싸이트](https://v3-docs.vuejs-korea.org/guide/reusability/plugins.html#introduction)
>>
>> - 여러 Component에서 공통으로 사용할 수 있는 공통의 함수를 미리 정의해두고 플로그인처럼 바로 사용할 수 있다
>> - Global Plugin으로 사용하기 위해서는 다음의 샘플코드처럼 필수 사항을 준수해야 한다.

```javascript
// main.js
import { createApp } from 'vue'
const app = createApp({})
app.use(myPlugin, {
  // 선택적인 옵션
})

// myPlugin.js
const myPlugin = {
  install(app, options) {
    // 앱 환경설정
  }
}
```

- 다음은 i18n(Internationalization)에 대한 plugin sample 코드 이다
  
```javascript
// main.js
import i18nPlugin from './plugins/i18n'
import en from './i18n/en'
import ko from './i18n/ko'

const i18nStrings = { en, ko }
app.use(i18nPlugin, i18nStrings)

// en.js
const i18nEN = {
  hi: 'Hello',
  search: 'Search',
  save: 'Save',
  welcome: 'Welcome, {name}',
  welcome1: 'Welcome, ',
  welcome2: ''
}

export default i18nEN

// ko.js
const i18nEN = {
  hi: '안녕하세요',
  search: '조회',
  save: '저장',
  welcome: '환영합니다. {name}님.',
  welcome1: '환영합니다.',
  welcome2: '님',
  welcome3: '환영합니다. {name}님({email}).'
}

export default i18nEN

// i18n.js
/* eslint-disable */
export default {
  install: (app, options) => {
    app.config.globalProperties.$translate = (key, params = {}) =>
      // en.hi => ['en','hi']
      key
        .split('.')
        .reduce((o, i) => {
          if (o) return o[i]
        }, options)
        .replace(/{\w+}/g, (match) => params[match.slice(1, -1)])
  }
}

// PluginView.vue
<template>
  <div>
    <h1>
      {{ $translate(`${userInfo.lang}.welcome1`) }} {{ userInfo.name
      }}{{ $translate(`${userInfo.lang}.welcome2`) }}
    </h1>
    <h1>
      {{ $translate(`${userInfo.lang}.welcome`, userInfo) }}
    </h1>
    <h1>
      {{ $translate(`${userInfo.lang}.welcome3`, userInfo) }}
    </h1>
    <h1>{{ $translate(`${userInfo.lang}.hi`) }}</h1>
    <!-- <h1>{{ $translate('ko.hi') }}</h1> -->
    <!-- <button>{{ $translate('ko.search') }}</button> -->
    <button>{{ $translate(`${userInfo.lang}.search`) }}</button>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      userInfo: {
        name: 'John Doe',
        email: 'john@gmail.com',
        lang: 'ko'
      }
    }
  }
}
</script>
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