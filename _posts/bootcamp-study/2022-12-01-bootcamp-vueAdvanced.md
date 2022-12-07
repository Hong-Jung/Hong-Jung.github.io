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

- 코드나 기능의 컴폰넌트화의 방식중에 하나이며, 플러그인으로 사용할 함수나 모듈은 `install(app, options)`를 정의하고 사용한다.

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
  welcome2: '',
  welcome3: 'Welcome. {name}({email}).'
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
```

<img src="./../../assets/images/posts/bootcamp005/plugin-1.png" width="80%" align="center"/>

# 5. Vuex

- Vuex는 모든 컴포넌트의 중앙 집중식 저장소 기능을 제공하며, Vuex에 저장된 데이터는 쉽게 바꿀 수 없으며 특정 함수(mutations, actions)를 통해서만 변경이 가능하고 변경 상태를 관리할 수 있다.
- `vuex-persistedstate`와 `vue-cookies` plugin 설치시 문제 발생시 다음의 명령어로 설치 

```command
npm i vuex-persistedstate --legacy-peer-deps
npm i vue-cookies --legacy-peer-deps
```

> **IMPORTANT**
>> [Vue.js Vuex 국문 참고 사이트](https://v3-docs.vuejs-korea.org/guide/scaling-up/state-management.html)<br/>
>> [Vue.js Vuex 영문 참고 사이트](https://vuex.vuejs.org/)
>>
>> - state : 데이터 저장소 (`this.$store.state.xxx`)
>> - getters : Store를 위한 computed(값의 변경을 즉시 알 수 있음) / 변수와 같이 사용될 수 있다. (`this.$store.getters.xxx`)
>> - mutations : 상태(state)를 변경시킬 수 있는 유일한 방법(함수) (`this.$store.commit('mutation name', parameter)`)
>> - actions : 정의된 함수에서는 mutations에 정의한 함수를 커밋(commit)시켜 state를 변경, 비동기 처리가 가능(DB 작업에 가능 많이 사용) (`this.$store.dispatch('action name', parameter)`)
>> - modules : store로 관리할 파일이나 저장소가 많아질 경우 모듈화하여 참조 사용 (`참조당하는 모듈에서는 반드시 namespaced:true 옵션 설정하고, 참조하는 모듈에서는 반드시 modules: { 참조키값: 참조모듈}) 정의 필요 / 실제 참조하여 사용하는 모듈에서는 '참조모듈/함수,변수명'('todo/dodosCount')형식으로 사용 필요`)
>> - 상태값 영구 관리를 위한 `persistedstate` 방법 : `'vue-persistedstate'` 참조 및 설치, `plugin` 정의
>> - 상태값 설정 시간만큼 관리를 위한 `cookie` 방법 : `'vue-cookies'` 참조 및 설치, `VueCookies` 접근

<img src="https://vuex.vuejs.org/vuex.png" width="90%" align="center"/>

```javascript
// store > index.js
import { createStore } from 'vuex'
import { todo } from './todo' // 모듈화를 위한 todo 참조
import { user } from './user' // 모듈화를 위한 user 참조
import persistedstate from 'vuex-persistedstate' // 상태값 영구 보존을 위한 플로그인 참조

export default createStore({
  modules: {
    todo: todo,
    user: user
  },
  plugins: [persistedstate({ paths: ['todo.todos'] })] // 영구 사용을 위해서는 반드시 지정되어야 함
})
```

```javascript
// todo.js for persistedstate(영구 상태값 저장을 위함)
export const todo = {
  // 중앙 데이터 저장소
  namespaced: true,
  state() {
    return {
      todos: [
        { id: 1, title: 'todo 1', done: true },
        { id: 2, title: 'todo 2', done: false },
        { id: 3, title: 'todo 3', done: false }
      ]
    }
  },
  // Store를 위한 computed라고 생각하면 됨.
  getters: {
    todosCount(state) {
      return state.todos.length
    },
    doneTodosCount(state) {
      return state.todos.filter((todo) => todo.done).length
    },
    notDoneTodosCount(state) {
      return state.todos.filter((todo) => !todo.done).length
    }
  },
  // 상태(state)를 변경시킬 수 있는 유일한 방법(함수)
  mutations: {
    add(state, item) {
      state.todos.push(item)
    },
    remove(state, id) {
      state.todos = state.todos.filter((todo) => todo.id !== id)
    },
    doneYN(state, doneStatus) {
      state.todos.filter((todo) => todo.id === doneStatus.id)[0].done =
        doneStatus.done
    }
  },
  // mutations 하고 비슷한데,
  // actions에 정의된 함수에서는 결국은 mutations에 정의한 함수를 커밋(commit)시켜서 state를 변경
  // 비동기 처리가 가능
  actions: {
    add({ commit }, item) {
      // const {commit, state} = context
      // context.commit, context.state

      // 서버랑 통신. fetch, axios
      commit('add', item)
    }
    // add2: async ({ commit }, item) => {
    //   await fetch('', {})
    // }
  }
}
```

```javascript
// user.js for cookie 사용을 위함
import VueCookies from 'vue-cookies'

export const user = {
  // 중앙 데이터 저장소
  namespaced: true,
  state() {
    return {
      userInfo: {
        name: '',
        email: '',
        phone: '',
        lang: ''
      }
    }
  },
  // Store를 위한 computed라고 생각하면 됨.
  getters: {
    isLogin(state) {
      if (VueCookies.get('userInfo')) {
        return true
      } else {
        return false
      }
    },
    isKakaoLogin() {
      if (window.Kakao.Auth.getAccessToken()) {
        return true
      } else {
        return false
      }
    }
  },
  // 상태(state)를 변경시킬 수 있는 유일한 방법(함수)
  mutations: {
    setUserInfo(state, userInfo) {
      console.log(userInfo)
      state.userInfo = userInfo
      VueCookies.set('userInfo', userInfo, '30s')
    },
    clearUserInfo(state) {
      state.userInfo = {}
      VueCookies.remove('userInfo')
    },
    getUserInfo(state) {
      if (VueCookies.get('userInfo')) {
        return state.userInfo
      } else {
        return {}
      }
    }
  },
  actions: {}
}
```

```html
// TodoView.vue
<template>
  <div>
    <div>{{ todos }}</div>
    <div>할일 목록 전체수 : {{ todosCount }}</div>
    <div>완료 목록 수 : {{ doneTodosCount }}</div>
    <div>미완료 목록 수 : {{ notDoneTodosCount }}</div>

    <div>
      <label for="todo" class="form-label">할일</label>
      <input type="text" name="" id="todo" class="form-control" v-model="todo" />
      <button class="btn btn-primary" v-on:click="addItem">추가(mutation)</button>
      <button class="btn btn-primary" @click="addItem2">추가(action)</button>
    </div>

    <div>
      <table class="table table-bordered table-striped">
        <thead>
          <tr>
            <th>Todo ID</th>
            <th>할일</th>
            <th>완료여부</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-bind:key="todo.id" v-for="todo in todos">
            <td>{{ todo.id }}</td>
            <td>{{ todo.title }}</td>
            <td>
              <div class="form-check form-switch">
                <input
                  class="form-check-input"
                  type="checkbox"
                  role="switch"
                  id="flexSwitchCheckChecked"
                  v-bind:checked="todo.done"
                  v-on:change="doneYN(todo.id, $event)"
                />
              </div>
            </td>
            <td><button class="btn btn-danger btn-sm" v-on:click="removeItem(todo.id)">삭제</button></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      todo: ''
    }
  },
  computed: {
    // namespace 사용으로 지정된 modules에 정의된 store 오브젝트 접근법
    todos() {
      return this.$store.state.todo.todos
    },
    todosCount() {
      return this.$store.getters['todo/todosCount']
    },
    doneTodosCount() {
      return this.$store.getters['todo/doneTodosCount']
    },
    notDoneTodosCount() {
      return this.$store.getters['todo/notDoneTodosCount']
    }
    // state나 module 없이 바로 사용하는 경우 다음과 같은 코드로 작성
    // ,
    // todos() {
    //   return this.$store.state.todos
    // },
    // todosCount() {
    //   return this.$store.getters.todosCount
    // },
    // doneTodosCount() {
    //   return this.$store.getters.doneTodosCount
    // },
    // notDoneTodosCount() {
    //   return this.$store.getters.notDoneTodosCount
    // }
  },
  methods: {
    // module 사용하는 코드 샘플
    addItem() {
      this.$store.commit('todo/add', { id: 4, title: this.todo, done: false })
    },
    removeItem(id) {
      this.$store.commit('todo/remove', id)
    },
    doneYN(id, event) {
      this.$store.commit('todo/doneYN', { id: id, done: !event.target.checked })
    },
    addItem2() {
      this.$store.dispatch('todo/add', { id: 4, title: this.todo, done: false })
    }

    //state나 module 없이 바로 사용하는 경우
    // addItem() {
    //   this.$store.commit('add', { id: 4, title: this.todo, done: false })
    // },
    // removeItem(id) {
    //   this.$store.commit('remove', id)
    // },
    // doneYN(id, event) {
    //   this.$store.commit('doneYN', { id: id, done: event.target.checked })
    // }
  }
}
</script>
```

```html
<!-- LoginView.vue -->
<template>
  <main class="form-signin w-100 m-auto">
    <div>
      <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

      <div class="form-floating">
        <input
          type="email"
          class="form-control"
          id="floatingInput"
          placeholder="name@example.com"
        />
        <label for="floatingInput">Email address</label>
      </div>
      <div class="form-floating">
        <input
          type="password"
          class="form-control"
          id="floatingPassword"
          placeholder="Password"
        />
        <label for="floatingPassword">Password</label>
      </div>

      <div class="checkbox mb-3">
        <label>
          <input type="checkbox" value="remember-me" /> Remember me
        </label>
      </div>
      <button class="w-100 btn btn-lg btn-primary" @click="login">
        Sign in
      </button>
      <p class="mt-5 mb-3 text-muted">&copy; 2017–2022</p>
    </div>
  </main>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      sampleData: ''
    }
  },
  methods: {
    login() {
      this.$store.commit('user/setUserInfo', {
        name: 'John Doe',
        email: 'john@gmail.com',
        phone: '010-0000-0000',
        lang: 'ko'
      })
    }
  }
}
</script>
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