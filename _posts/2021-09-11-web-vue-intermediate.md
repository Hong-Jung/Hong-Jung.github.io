---
title:  "Vue Intermediate"
excerpt: "장기효 강사의 Vue 중급 강좌를 수강하며 학습 목적으로 작성된 자료 입니다. 출처는 하단을 참고 바랍니다."
comments: true
header:
  teaser: 

categories:
  - web
tags:
  - [Blog, Vue]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2021-09-11
last_modified_at: 2021-10-03
---

## 1. 강의 Agenda
### 1.1 개발환경 구성

## 2. Todo App - 프로젝트 소개 및 구성
### 2.1 To-do App 소개

## 3. Todo App - 프로젝트 구현
### 3.1 콤포넌트 설계 및 구현
### 3.2 index.html CDN 추가
  * Viewport : ```<meta name="viewport" content="width=device-width, initial-scale=1.0">``` / [Responsive Web Design Viewport](https://www.w3schools.com/css/css_rwd_viewport.asp)
  * 파비콘 : [Favicon & App Icon Generator](https://www.favicon-generator.org/)
  * awesome icon : [Font Awesome](https://fontawesome.com/v5.15/icons?d=gallery&p=2)
  * google font ubuntu : [Google Fonts](https://fonts.google.com/specimen/Ubuntu#standard-styles)
### 3.3 component 구현
  * TodoHeader
  * TodoInput
    - localstorage mdn(Mozilla Developer Network) : [Window.localStorage - Web API](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage)
    - splice() API mdn(Mozilla Developer Network) : [Array.prototype.splice() - JavaScript](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
    - 폰트 어썸 링크 : [Font Awesome](https://fontawesome.com/)
    - <img src="../../assets/images/posts/vue-intermediate/3.3_fontawesome.png" width="60%" height="30%" title="Font Awesome" alt="Font Awesome"/>
    - vue lifecycle
    - <img src="../../assets/images/posts/vue-intermediate/3.3_vue_lifecycle.png" width="60%" height="30%" title="Vue Life Cycle" alt="Vue Life Cycle"/>

## 4. Todo App - 애플리케이션 구조 개선하기
### 4.1 기존 애플리케이션
  * <img src="../../assets/images/posts/vue-intermediate/4.1_as-is.png" width="60%" height="30%" title="기존 구조" alt="기존 구조"/>
### 4.2 변경 애플리케이션
  * <img src="../../assets/images/posts/vue-intermediate/4.2_to-be.png" width="60%" height="30%" title="변경 구조" alt="변경 구조"/>

## 5. Todo App - 사용자 경험 개선
  * 모달 컴포넌트 적용 : [모달 컴포넌트](https://kr.vuejs.org/v2/examples/modal.html)
  * slot : 일부 UI 요소들을 재사용 할 수 있다. [Slots](https://vuejs.org/v2/guide/components-slots.html#Named-Slots-with-the-slot-Attribute)
  * Transitions & Animation : [Link](https://v3.vuejs.org/guide/transitions-overview.html#class-based-animations-transitions)
    * List Transitions : [Link - List Transitions](https://v3.vuejs.org/guide/transitions-list.html#list-entering-leaving-transitions)
    * <img src="../../assets/images/posts/vue-intermediate/5.1_enter_leave_active.png" width="80%" height="30%" title="Enter/Leave Active" alt="Enter/Leave Active"/>

## 6. ES6 for Vue.js - 오리엔테이션
### 6.1 ES6(ECMAScript2015) : [최신의 자바스크립트 문법](https://babeljs.io/docs/en/learn)
  * 2015년은 ES5(2009년)이래로 진행한 첫 메이저 업데이트가 승인됨
  * 최신 프론트앤드인 Angular, React, Vue에서 권고
  * [Babel](https://babeljs.io/docs/en/) : 자바스크립트 컴파일러, 구번전의 브라우저의 경우 호환성을 위해서 Transpiling 필요

## 7. ES6 for Vue.js - const & let
### 7.1 const & let : 변수 선언 방식
  * { }로 변수의 스콥을 제한 (ES5의 경우 { }와 상관없이 스콥이 설정됨)
  * const : 상수의 개념으로 선언 후 변경 할 수 없음
  * let : 선언한 변수는 재 선언 할 수 없음
### 7.2 ES5의 Hoisting
  * <img src="../../assets/images/posts/vue-intermediate/7.2_Hoisting.png" width="80%" height="30%" title="Hoisting" alt="Hoisting"/>
### 7.3 ES6의 { } Scope 샘플
  * <img src="../../assets/images/posts/vue-intermediate/7.3_Scope.png" width="50%" height="30%" title="{} Scope" alt="{} Scope"/>
### 7.4 ES6의 const 샘플
  * <img src="../../assets/images/posts/vue-intermediate/7.4_const.png" width="50%" height="30%" title="const" alt="const"/>
### 7.5 ES6의 let 샘플
  * <img src="../../assets/images/posts/vue-intermediate/7.5_let.png" width="60%" height="30%" title="let" alt="let"/>
### 7.6 ES6의 const, let 샘플
  * <img src="../../assets/images/posts/vue-intermediate/7.6_const_let.png" width="80%" height="30%" title="const & let" alt="const & let"/>

## 8. ES6 for Vue.js - 화살표 함수
  ### 8.1 Arrow Function : 함수 정의시 “function” 키워드 대신 “=>”로 사용, “콜백 함수”의 간결화
  * <img src="../../assets/images/posts/vue-intermediate/8.1_arrow_1.png" width="40%" height="30%" title="Arrow Fuction (1)" alt="Arrow Fuction (1)"/>
  * <img src="../../assets/images/posts/vue-intermediate/8.1_arrow_2.png" width="40%" height="30%" title="Arrow Fuction (2)" alt="Arrow Fuction (2)"/>

## 9. ES6 for Vue.js - Enhanced Object Literals (향상된 객체 리터럴)
### 9.1 객체의 속성을 메서드로 사용할 때 “function” 예약어를 생략
  * <img src="../../assets/images/posts/vue-intermediate/9.1_function.png" width="40%" height="30%" title="function" alt="function"/>
### 9.2 객체의 속석명과 값 명이 동일할 때 축약 가능
  * <img src="../../assets/images/posts/vue-intermediate/9.2_contraction.png" width="40%" height="30%" title="contraction" alt="contraction"/>

## 10. ES6 for Vue.js - Modules
### Javascript 모듈 로더 Library(AMD, Commons JS) 기능을 js 언어 자체에서 지원
### 호출되지 전가지는 코드 실행과 동작을 하지 않는 특징
  * <img src="../../assets/images/posts/vue-intermediate/10.1_1.png" width="40%" height="30%" title="modules" alt="modules"/>
  * <img src="../../assets/images/posts/vue-intermediate/10.1_2.png" width="80%" height="30%" title="defult export" alt="defult export"/>


## 11. Vuex - 소개
### 11.1 복잡한 App의 Component 관리 (많은 수의 Component를 관리하는 상태 관리 패턴(라이브러리))
### 11.2 React의 “Flux” 패턴과 유사
### 11.3 Flux : MVC 패턴의 복잡한 데이터 흐름 문제 해결을 위한 패턴(Unidirectional data flow)
* <img src="../../assets/images/posts/vue-intermediate/11.3_flux.png" width="80%" height="30%" title="flux" alt="flux"/>
* <img src="../../assets/images/posts/vue-intermediate/11.3_vuex.png" width="100%" height="30%" title="vuex" alt="vuex"/>
  
### 11.4 Vuex 컨셉
* State : 컴포넌트 간에 데이터 공유 “data()”
* View : 데이터를 표시하는 화면 “template”
* Action : 사용자의 입력에 따라 데이터를 변경 “methods”
* <img src="../../assets/images/posts/vue-intermediate/11.4_vuex.png" width="50%" height="30%" title="vuex" alt="vuex"/>
* <img src="../../assets/images/posts/vue-intermediate/11.4_mutation.png" width="80%" height="30%" title="mutation" alt="mutation"/>
  
### 11.5 Vuex 구조
  * 컴포넌트 > 비동기 로직 > 동기 로직 > 상태
  * <img src="../../assets/images/posts/vue-intermediate/11.5_vuex_1.png" width="80%" height="30%" title="Vuex" alt="Vuex"/>
  * <img src="../../assets/images/posts/vue-intermediate/11.5_vuex_2.png" width="80%" height="30%" title="Vuex" alt="Vuex"/>

## 12. Vuex- 주요 기술 요소
### 12.1 Vuex 설치
  * Single File Component에서는 NPM 방식으로 라이브러리 설치
  
```
npm install vuex --save; // ES6과 사용해야 많은 추가적인 기능을 사용 가능
```
  * Vuex 등록
  
```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex);

export const store = new Vuex.Store({

});
```
### 12.2 기술 요소
  * state : 여러 컴포넌트에 공유되는 데이터 “data”
  
```
// Vue
data: {
  message: 'hello vue.js'
}
// Vuex
state: {
  message: 'hello vue.js'
}
```

```
// Vue
<p>{{ message }}</p>

// Vuex
<p>{{ this.$store.state.message }}</p>
```

  <img src="../../assets/images/posts/vue-intermediate/12.1.png" width="100%" height="30%" title="Vuex" alt="Vuex"/> 
  * “state”는 왜 “this.$store.state.변수++;”와 같이 직접 변경하지 않고 “mutations”를 호출하여 접근 및 변경 하는가?
    * 일관성 있는 “state” 변수의 관리를 위함 (여러 컴포넌트에서 각자 변경하면 추척이 불가능)
    * 뷰의 반응성을 거스르지 않게 명시적으로 관리함으로 “반응성, 디버깅, 테스팅” 효율 향상

### 12.3 getters : 연사된 state 값을 접근하는 속성 “computed”
```
// store.js
state: {
  num: 10
}
getters: {
  getNumber(state) {
    return state.num;
  },
  getDoubleNumber(state) {
    return state.num * 2;
  }
}
{{}}
```

```
<p> {{ this.$store.getters.getNumber }} </p>
<p> {{ this.$store.getters.getDoubleNumber }} </p>
```

### 12.4 mutations : “state” 값을 변경하는 이벤트 로직, 메서드 “methods”
  * “state” 값을 변경할 수 있는 “유일한 방법”이자 method
  * “commit()”으로 실행

```
// store.js
state: { num: 10 },
mutations: {
  printNumbers(state) {
    return state.num
  },
  sumNumbers(state, anotherNum) {
    return state.num + anotherNum;
  }
}

// App.vue
this.$store.commit('printNumbers');
this.$store.commit('sumNumbers', 20);
```

  * “commit()” 형식

```
// store.js
state: { storeNum: 10 },
mutations: {
  modifyState(state, payload) {
    console.log(payload.str);
    return state.storeNum += payload.num;
  }
}

// App.vue
this.$store.commit('modifyState', {
  str: 'this is commit parameter',
  num: 20
});
```

### 12.5 vuex에서 actions를 제외한 사용 샘플
  * <img src="../../assets/images/posts/vue-intermediate/12.5_vuex_actions.png" width="100%" height="30%" title="Vuex Actions" alt="Vuex Actions"/> 

## 12.6 actions : 비동기 처리 로직을 선언하는 메서드 “async methods”
  * 비동기 처리를 위한 메서드로 비동기 로직을 위한 mutations
  * actions : data request, promise, ES6 async
  * actions code sample #1
  
```
// store.js
state: {
  num: 10
},
mutations: {
  doubleNumber(state) {
    state.num * 2;
  }
},
actions: {
  delayDoubleNumber(context) {
    // context 파라메터를 통하여 store의 메서드와 속성에 접근
    context.commit('doubleNumber');
  }
}

// App.vue
this.$store.dispatch('delayDoubleNumber');
```

  * [Promise 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/), [자바스크립트 비동기 처리 이해하기](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)
  * actions code sample #2
  
```
// store.js
mutations: {
  addCounter(state) {
    state.counter++;
  }
},
actions: {
  delayedAddCounter(context) {
    setTimeout(() => context.commit('addCounter'), 2000);
  }
}

// App.vue
methods: {
  incrementCounter() {
    this.$store.dispatch('delayedAddCounter');
  }
}
```

  * actions code sample #3
  
```
// store.js
mutations: {
  setData(state, fetchedData) {
    state.product = fetchedData;
  }
},
actions: {
  fetchProductData(context) {
    return axios.get('https://domail.com/products/1')
                .then(response => context.commit('setData', response));
  }
}

// App.vue
methods: {
  getProduct() {
    this.$store.dispatch('fetchProductData');
  }
}
```

  * 비동기 메서드인 actions를 사용하는 이유??
    * 어떤 콤포넌트에서 state를 호출하고 변경한건지 확인이 어려움
    * <img src="../../assets/images/posts/vue-intermediate/12.5_actions.png" width="70%" height="30%" title="Actions" alt="Actions"/>

## 13. Vuex - 헬퍼 함수
### 13.1 Vuex Helper
  * mapState, mapGetters, mapMutations, mapActions와 같이 기존의 Vuex의 Helper
  
### 13.2 Help "..." Sample
  * helper import 후 “…”(ES6의 object spread operator) 사용 샘플
  
```
// App.vue
import { mapState, mapGetters, mapMutations, mapActions } from 'vuex'

export default {
  computed() {
    ...mapState(['num']), ...mapGetters(['countedNum'])
  },
  methods: {
    ...mapMutations(['clickBtn']), ...mapActions(['asyncClickBtn'])
  }
}
```

### 13.3 state
  * mapState : Vuex에 선언한 state 속성을 뷰 컴포넌트에 쉽게 연결해 주는 Helper
  * mapState Sample
  
```
// App.vue
import { mapState } from 'vuex'

computed() {
  ...mapState(['num']); 
  // num() { return this.$store.state.num; }
}

<!-- 'num'으로 바로 접근 가능 -->
<!--<p>{{ this.$store.state.num }}</p>-->
<p>{{ this.num }}</p>

// store.js
state: {
  num: 10
}
```

### 13.4 getters
  * mapGetters : Vuex 선언한 getters 속성을 뷰 컴포넌트에 더 쉽게 연결해 주는 Helper
  * mapGetters Sample
  
```
// App.vue
import { mapGetters } from 'vuex'

computed() {
  ...mapGetters(['reverseMessage']);
}

<!--<p>{{ this.$store.getters.reverseMessage }}</p>-->
<p>{{ this.reverseMessage }}</p>

// store.js
getters: {
  reverseMessage(state) {
    return state.msg.split('').reverse().join('');
  }
}
```

### 13.5 mapState & mapGetters sample
  * <img src="../../assets/images/posts/vue-intermediate/13.5.png" width="100%" height="30%" title="mapState & mapGetters" alt="mapState & mapGetters"/>

### 13.6 mutations
  * mapMutations : Vuex에 선언한 mutations 속성을 vue component에서 쉽게 사용할 수 있는 helper
  * mapMutations Sample
  
```
// App.vue
import { mapMutations } from 'vuex'

methods: {
  ...mapMutations(['clickBtn']),
  authLogin() {},
  displayTable() {}
}

<button @click="clickBtn">popup message</button>

// store.js
mutations: {
  clickBtn(state) {
    alert(state.msg);
  }
}
```

### 13.7 actions
  * mapActions : Vuex에 선언한 actions 속성을 vue component에서 쉽게 사용할 수 있는 helper
  * mapActions Sample
  
```
// App.vue
import { mapActions } from 'vuex'

methods: {
  ...mapActions(['delayClickBtn']),
}

<button @click="delayClickBtn">delay popup message</button>

// store.js
actions: {
  delayClickBtn(context) {
    setTimeout(() => context.commit('clickBtn'), 2000);
  }
}
```

### 13.8 helper의 문법 2가지
  * Vuex에 선언한 속성을 그대로 컴포넌트에 연결하는 문법
  
```
// 배열 리터럴
...mapMutations([
  'clickBtn', // 'clickBtn': clickBtn
  'addNumber' // addNumber(인자)
])
```

  * Vuex에 선언한 속성을 컴포넌트의 특정 메서드에 연결하는 문법
  
```
// 객체 리터럴
...mapMutations({
  popupMsg: 'clickBtn' // 컴포넌트 메서드 명 : store의 뮤테이션 명
})
```

### 13.9 mapMutations & mapActions sample
  * <img src="../../assets/images/posts/vue-intermediate/13.9.png" width="100%" height="30%" title="mapMutations & mapActions" alt="mapMutations & mapActions"/>
  
### 13.10 Helper의 간결함
  * <img src="../../assets/images/posts/vue-intermediate/13.10.png" width="100%" height="30%" title="간결함" alt="간결함"/>

## 14. Vuex - 프로젝트 구조화 및 모듈화
  * 다음의 store를 모듈화 방안
  
```
// store.js
import Vue from 'vue'
import Vuex from 'vuex'

export const store = new Vuex.Store({
  state: {},
  getters: {},
  mutations: {},
  actions: {}
});
```

  * 모듈화 1
  
```
import Vue from 'vue'
import Vuex from 'vuex'
import * as getters from 'store/getters.js'
import * as mutations from 'store/mutations.js'
import * as actions from 'store/actions.js'

export const store = new Vuex.Store({
  state: {},
  getters: getters,
  mutations: mutations,
  actions: actions
});
```

  * 모듈화 2
  
```
// store.js
import Vue from 'vue'
import Vuex from 'vuex'
import todo from 'modules/todo.js'

export const store = new Vuex.Store({
  modules: {
    modulesTodo: todo, // modules name: modules file name
    todo // todo: todo
  }  
});

// todo.js
const state = {}
const getters = {}
const mutations = {}
const actions = {}
```

## 15. 출처

  * [인프런](https://www.inflearn.com/course/vue-pwa-vue-js-%EC%A4%91%EA%B8%89/dashboard)