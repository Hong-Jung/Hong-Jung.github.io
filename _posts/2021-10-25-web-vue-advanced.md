---
title:  "Vue Advanced"
excerpt: "장기효 강사의 Vue 고급 강좌를 수강하며 학습 목적으로 작성된 자료 입니다. 출처는 하단을 참고 바랍니다."
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
 
date: 2021-10-25
last_modified_at: 2021-10-25
---

<img src="../../assets/images/posts/vue-advanced/vue-advanced.png" width="80%"/>

## 1. Study Agenda

### 1.1 Summary
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-1.init`**
- Vuejs의 고급 모듈로 실습과 리펙토링 위주의 학습
- 각 주요 과정마다 `branch'를 만들어 사용할 예정
  - vue-advanced-1.init : 생성 ~ 1번째 세션 진입 전
  - vue-advanced-2.???? : 
- 오리지널 소스는 [Github](https://github.com/Hong-Jung/vue-advanced.git) 참고
- `branch` Naming Rules
  > Prefix : `vue-advanced-`<br/>
  > Name : `sequecnce.` + `brief class name`<br/>
  > Example : `vue-advanced-1.init`

### 1.2 개발 환경
- node js : LTS 버전
- Visual Studio Code : Vetur(SFP, 자동완성), TSLint & ESLint(TypeScript), Auto Close Tag, Material Icon Theme, Night Owl, Live Server
- Github
- Chrome & Vue devTool

### 1.3 Vue.js Style Guide
- Vue.js 사용에 코어팀의 공식 추천 스타일 가이드
  > Priority A : Essential<br/>
  > Priority B : Strongly Recommended<br/>
  > Priority C : Recommended<br/>
  > Priority D : Use with Caution
- [Vue.js Style Guide](https://vuejs.org/v2/style-guide/#Multi-word-component-names-essential)

## 2. Application Development

### 2.1 Introduce Application & API
- 소개
  - [Hacker News](https://news.ycombinator.com/)의 특정 몇개의 게시판(News, Ask, Jobs) 제작
- Router Design
  - 컴포넌트 기반의 설계 할 수 있도록
  - Hacker News의 게시판 중 `News`, `Ask`, `Jobs` 3개 개발
    > News 리스트<br/>
    > Ask 리스트<br/>
    > Jobs 리스트<br/>
    > 상세 페이지<br/>
    > 사용자 정보
- API(Application Programming Interface)
  - [HNPWA API](https://github.com/tastejs/hacker-news-pwas/blob/master/docs/api.md) API Document
- Vue CLI(Command Line Interface) 2.x, 3.x
  - `npm i -g @vue/cli-init` : `vue init...` 명령어를 위한 global 설치
  - *기존의 `Github`소스를 다운받은 후 `npm i` 명령어를 사용하여 `package.json`의 dependencies 설치 후 `npm run serve` 실행 필요*
    
|     Feature      | CLI v2.x                                                                                        | CLI v3.x                                                                                                                                                                |
| :--------------: | :---------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|    **명령어**    | `vue init '프로젝트 템플릿 이름' '파일 위치'`<br/>*Sample* : `vue init webpack-simple vue-news` | `vue create '프로젝트 이름'`<br/>*Sample* : `vue create vue-cli3`                                                                                                       |
| **Webpack 설정** | 노출 O<br/>`webpack.config.js`을 직접 수정                                                      | <span style="color:hotpink">*노출 X*</span><br/>`vue.config.js`의 `configureWebpack`로 설정 가능([Link](https://cli.vuejs.org/guide/webpack.html#simple-configuration)) |
| **Project 구성** | `Github`의 Template 다운로드                                                                    | `Plugin` 기반으로 추가                                                                                                                                                  |
|   **ES6 이해**   | 필요 X                                                                                          | <span style="color:hotpink">*필요 O*<span>                                                                                                                              |

### 2.2 Project Setup
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-1.init`**
- Vue CLI 설치 (프로젝트의 기본 골격을 생성)
  - Command : `vue create '프로젝트 이름'`
  - Sample : `vue create vue-news`
    ```
    vue create vue-news // vue cli 설치
    npm run serve // service 기동
    ```	
- ESLint?
  > 린트(lint) 또는 린터(linter)는 소스 코드를 분석하여 프로그램 오류, 버그, 스타일 오류, 의심스러운 구조체에 표시(flag)를 달아놓기 위한 도구들을 가리킨다.<br/>
  > - `vue.config.js` 파일에 `lintOnSave` 속성으로 조정 가능<br/>
  > - [Vue CLI - Configuration Reference](https://cli.vuejs.org/config/#global-cli-config)

### 2.3 Router
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-2.router`**
- `라우팅`을 목적으로하며 다음과 같은 키워드가 중요하다
  > 전용 `router` 파일<br/>
  > `routes`, `path`, `component`, `redirect`, `mode`, `router-view`, `router-link`
- Router Install
  > `npm i vue-router --save` 명령어로 `router` 설치<br/>
  > `package.json` > `dependencies`에 vue-router 설정 됨
  - vue-router 사용 예제 (*router 파일이 많아질 경우 복잡*)
    ```javascript
    // main.js
    import VueRouter from 'vue-router';
    Vue.use(VueRouter);
    const router = new VueRouter({
      routes: [
        // 라우팅할 파일들
      ]
    });
    ```
  - `router` folder 만들어 사용 권고 (*vue-router 개선*)
    - 별도의 `router`를 위한 파일을 정의하여 관리
      ```javascript
      // 0.1 : router 전용 파일을 생성하고 정의 한다.
      // -routes > index.js------------------------------------------
      // import essential
      import Vue from 'vue';
      import VueRouter from 'vue-router';
      // import vue
      import NewsView from '../views/NewsView.vue';
      import AskView from '../views/AskView.vue';
      import JobsView from '../views/JobsView.vue';

      Vue.use(VueRouter);

      export const router = new VueRouter({
          routes: [
              {
                  // path : url 주소
                  path: '/news', 
                  // component : url 주소로 이동시 나타날 컴포넌트
                  // 보여질 vue 페이지
                  component: NewsView, 
              },
              {
                  path: '/ask',
                  component: AskView,
              },
              {
                  path: '/jobs',
                  component: JobsView,
              }
          ]
      });
      // -router > index.js------------------------------------------

      // 0.2 : *.vue 페이지 들을 생성 한다.
      // -*.vue------------------------------------------
      // views > NewsView.vue, AskView.vue, JobsView.vue 파일 생성
      // '스캐폴드' 기능을 사용하여 기본 vue 템플릿으로 생성
      // -*.vue------------------------------------------

      // 0.3 : 정의된 router 를 연결 한다.
      // -main.js------------------------------------------
      // 정의된 router를 import하고 전역 인스턴스에 설정 한다.
      // import router
      import { router } from './routes/index.js';

      new Vue({
        render: h => h(App),
        router,
      }).$mount('#app')
      // -main.js------------------------------------------

      // 0.4 : App.vue에 router-view 태그를 추가
      // -App.vue------------------------------------------
      <template>
        <div id="app">
          <tool-bar></tool-bar> //케밥 케이스 컴포넌트 스타일 가이드
          <router-view></router-view>
        </div>
      </template>

      <script>
      import ToolBar from './components/ToolBar.vue';

      export default {
        components: {
          ToolBar,
        },
      }
      </script>
      // -App.vue------------------------------------------
      ```
- `redirect` & `router-link` Attribute
  - `redirect` : URL을 바로 이동 시킴
    ```javascript
    export const router = new VueRouter({
        mode: 'history', // url에 '#'이 붙지 않음
        routes: [
            {
                path: '/',
                redirect: '/news',
            },
            // 기존과 동일
        ]
    });
    ```
  - `router-link` : vue 내부 적으로 `a` 태크로 변경 시킴
    ```html
    <!--ToolBar.vue-->
    <template>
      <div class="header">
          <router-link to="/news">News</router-link> | 
          <router-link to="/ask">Ask</router-link> | 
          <router-link to="/jobs">Jobs</router-link>
      </div>
    </template>
    <!--나머지 스타일 관련은 해당 파일 참조-->
    ```
- ES6 Modules
  - 변수의 Scope의 문제해결을 위하여, Export & Import 사용하여 `모듈화`
  - [ES6 Modules](https://hong-jung.github.io/web/web-vue-intermediate/#10-es6-for-vuejs---modules) 
- ES6 Enhanced Object Literal
  - `function` 예약어 및 `객체 속성 이름`과 `값 이름`이 같을 경우 생략 가능
  - [ES6 Enhanced Object Literal](https://hong-jung.github.io/web/web-vue-intermediate/#9-es6-for-vuejs---enhanced-object-literals-%ED%96%A5%EC%83%81%EB%90%9C-%EA%B0%9D%EC%B2%B4-%EB%A6%AC%ED%84%B0%EB%9F%B4)
	
### 2.4 API
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-3.api`**
- Mandatory Install
  - ```npm i axios --save```
- Hacker-News API URL : [URL](https://github.com/tastejs/hacker-news-pwas/blob/master/docs/api.md)
  - News : [News Link](https://api.hnpwa.com/v0/news/1.json)
  - Ask : [Ask Link](https://api.hnpwa.com/v0/ask/1.json)
  - Jobs : [Jobs Link](https://api.hnpwa.com/v0/jobs/1.json)
- `API`(Application Programming Interface) 어플리케이션간 프로그래밍 관점의  인터페이스
  > 주요한 용어<br/>
  > `routes`, `path`, `component`, `redirect`, `mode`, `router-view`, `router-link`
- `axios`를 활용하여 `hacker api` 사용
- API 개발 적용
  - `api` 전용 폴더를 생성하여 `import`할 라이브러리와 `API` 중앙에서 관리(기본 템플릿을 아래와 같이하며, 계속해서 확장해 간다)
    ```javascript
    import axios from 'axios';

    // 1. HTTP Request & Response와 관련된 기본 설정
    const config = {
        baseUrl: 'https://api.hnpwa.com/v0/'
    };

    // 2. API 함수들 정리
    function fetchNewList() {
        //return axios.get(config.baseUrl + 'news/1.json'); // javascript
        return axios.get(`${config.baseUrl}news/1.json`); // ES6
    };

    // 3. API Export
    export {
        fetchNewList
    }
    ```
- javascript `this`의 4가지 특징
  - 1번째
    - `window` 오브젝트의 경우 `최상단` 객체 이다.
    - <img src="../../assets/images/posts/vue-advanced/2.4. javascript_this_1.png" width="50%"/>
  - 2번째
    - `this`는 `window` 오브젝트를 지칭하며, 전역으로 사용된다.
    - <img src="../../assets/images/posts/vue-advanced/2.4. javascript_this_2.png" width="50%"/>
  - 3번째
    - 인스턴스를 생성하면 생성된 인스턴스가 `this`이며, 아닌경우 `window` 오브젝트가 `this`가 된다.
    - <img src="../../assets/images/posts/vue-advanced/2.4. javascript_this_3.png" width="50%"/>
  - 4번째
    - 기존의 `javascript` 문법은 함수 내에서 `data`에 계속해서 할당해서 사용하는 불편함에 있음으로 `ES6`의 `화살표 문법`을 사용하여 쉽게 사용 할 수 있다.
    - <img src="../../assets/images/posts/vue-advanced/2.4. javascript_this_4.png" width="100%"/>
- javascript 비동기 처리 `Callback`
  - [자바스크립트 비동기 처리](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)
  - 결과는 : `함수 결과`부터 실행되고 이후 `ajax` api 호출 결과 출력됨 (즉, 비동기 형식으로 실해됨)
    ```javascript
    <script>
        function fetchData() {
            // 1
            var result = [];

            // 2
            $.ajax({
                url: 'https://api.hnpwa.com/v0/news/1.json',
                success: function(data) {
                    console.log('reult of data call', data);
                    result = data;
                }
            });

            // 3
            console.log('함수 결과', result);
        }

        fetchData();
    </script>
    ```
  - 아래와 같이 `비동기 실행`에 대해서 이해하고 내부에서 처리해야 됨
    ```javascript
    <script>
        function fetchData() {
            // 1
            var result = [];

            // 2
            $.ajax({
                url: 'https://api.hnpwa.com/v0/news/1.json',
                success: function(data) {
                    console.log('reult of data call', data);
                    result = data;
                    console.log('함수 결과', result);
                }
            });

            // 3
            //console.log('함수 결과', result);
        }
        fetchData();
    </script>
    ```
- javascript 비동기 처리 `Promise`
  - [자바스크립 Promise 쉽게 이햏하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
  - [Promise MDN(Mozilla Developer Network)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  - `new Promise` 객체에 대해서만 `.then()`, `.catch()`를 추가 할 수 있다.
    ```javascript
    $.ajax(api 호출 로직)
    .then(성공시 로직)
    .catch(실패시 로직)
    ```
  - 하기와 같이 `callback` 함수를 `promise` api로 구현 할 수 있다.
  - `new Promise`, `resolve`, `then`
  - Promise States
    - Pending(대기) : 비동기 처리 로직이 아직 완료되지 않은 상태
    - Fulfilled(이행) : 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태
    - Rejected(실패) : 비동기 처리가 실패하거나 오류가 발생한 상태
      ```javascript
      <script>
            function callAjax() {
                return new Promise(function(resolve, rejet) {
                    $.ajax({
                        url: 'https://api.hnpwa.com/v0/news/1.json',
                        success: function(data) {
                            resolve(data);
                        }
                    });
                });
            }

            function fetchData() {
                var result = [];

                callAjax()
                .then(function(data) {
                    console.log('reult of data call', data);
                    result = data;
                    console.log('함수 결과', result);
                });
            }
            fetchData();
        </script>
      ```

### 2.5 Store
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-4.store`**
- `Vuex` 플러그이을 사용하여 `상태` 관리
  - <img src="../../assets/images/posts/vue-advanced/2.5 vuex as-is, to-be.png" width="80%"/>
- Mandatory Install
  - `npm i vuex` 를 사용해서 `vuex` 설치
  - <img src="../../assets/images/posts/vue-advanced/2.5 install vuex.png" width="70%"/>
- `store` 폴더를 생성하여 `vuex` 통합 관리 한다.
  ```javascript
  // main.js
  import Vue from 'vue'
  import App from './App.vue'
  import { router } from './routes/index.js'; // import router
  import { store } from './store/index.js'; // import store

  Vue.config.productionTip = false;

  new Vue({
    render: h => h(App),
    router,
    store, // store 정의
  }).$mount('#app')

  // store/index.js
  import Vue from 'vue';
  import Vuex from 'vuex';
  import { fetchNewsList } from '../api/index.js'; // backend api import

  Vue.use(Vuex);

  export const store = new Vuex.Store({
      // state : 전역 변수
      state: {
          news: []
      },
      // mutations : actions와 state를 연결 할당해 주는 역할
      // 첫번째 인자는 기본 state이고 나머지 인자는 호출한 함수에서 정의 한다.
      mutations: {
          SET_NEWS(state, data) {
              state.news = data;
          }
      },
      // actions : backend API 호출을 위한 함수
      // context.commit()를 사용하여 mutations을 호출 한다.
      // 첫번재 인자는 'mutations'의 이름이고 나머지 인자는 'mutations'로 넘길 인자이다.
      actions: {
          FETCH_NEWS(context) {
              fetchNewsList()
              .then(response => {
                  console.log(response);
                  //이때 'mutations의 'SET_NEWS'를 호출
                  context.commit('SET_NEWS', response.data); 
              })
              .catch(error => {
                  console.log(error);
              })
          }
      }
  });

  // NewsView.vue
  <template>
    <div>
      <!--this.$store.state로 state에 정의한 변수에 접근 한다.-->
      <div v-for="user in this.$store.state.news" :key="user.id">{{ user.title }}</div>
    </div>
  </template>

  <script>
  export default {
    created() {
      // $store의 dispatch('actions 이름')을 통하여 'actions'를 호출 한다.
      this.$store.dispatch('FETCH_NEWS');
    },
  }
  </script>
  ```
- 즉 !! 아래의 Vuex Flow 참고 (규칙이다)
  - <img src="../../assets/images/posts/vue-advanced/2.5 vuex flow.png" width="80%"/>
  - `Backend API`에서 호출된 비동기 형식의 함수를 `Actions(context)`에서 호출
  - `Actions`에서는 `context.commit('mutations name', '파라메터')`를 통하여 데이터를 `Mutations`의 `State`값에 할당
  - Vue페이지에서 `computed`와 `...mapGetters`를 사용하여 `state`에 쉽게 접근
    ```javascript
    // store/index.js
    getters: {
        fetchedAsks(state) {
            return state.asks;
        }
    },

    // views/AskView.vue
    <div v-for="item in fetchedAsks" :key="item.id">{{ item.title }}</div>

    computed: {
      ...mapGetters({
        fetchedAsks: 'fetchedAsks',
      }),
    },
    ```
  - `store`에 존재하는 많은 양의 `actions`, `mutations`, `state`, `getters`를 콤포넌트로 분리하여 사용
    ```javascript
    // store/index.js
    import state from './state.js';
    import getters from './getters.js';
    import mutations from './mutations.js';
    import actions from './actions.js';

    export const store = new Vuex.Store({
        state,
        getters,
        mutations,
        actions,
    });

    // store/state.js
    export default {
        news: [],
        asks: [],
        jobs: []
    }

    // store/getters.js
    export default {
        fetchedAsks(state) {
            return state.asks;
        }
    }

    // store/actions.js
    import { fetchNewsList, fetchAsksList, fetchJobsList } from '../api/index.js';

    export default {
        FETCH_NEWS(context) {
            fetchNewsList()
            .then(response => {
                context.commit('SET_NEWS', response.data);
            })
            .catch(error => {
                console.log(error);
            })
        },
        FETCH_ASK({ commit }) {
            fetchAsksList()
            .then(({ data }) => {
                commit('SET_ASKS', data);
            })
            .catch(error => {
                console.log(error);
            })
        },
        FETCH_JOBS({ commit }) {
            fetchJobsList()
            .then(({ data }) => {
                commit('SET_JOBS', data);
            })
            .catch(error => {
                console.log(error);
            })
        }
    }

    // store/mutations.js
    export default {
        SET_NEWS(state, data) {
            state.news = data;
        },
        SET_ASKS(state, data) {
            state.asks = data;
        },
        SET_JOBS(state, data) {
            state.jobs = data;
        }
    }
    ```
- [Vuex Data Flow](https://vuex.vuejs.org/)

## 3. Application Refactoring 

### 3.1 Router
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-5.router`**
- [Dynamic Route Matching](https://router.vuejs.org/guide/essentials/dynamic-matching.html)
- [ES6 템플릿 리터럴 설명 글(e북)](https://joshua1988.github.io/es6-online-book/template-literal.html)
  - `static`한 파라메터가 아닌 `dynamic`한 파라메터를 사용할 경우
- 참고 사이트
  - [Font awesome 사이트](https://fontawesome.com/)
  - [v-html API 문서](https://vuejs.org/v2/api/#v-html)
  - [v-html과 데이터 바인딩 차이점 문서](https://vuejs.org/v2/guide/syntax.html#Raw-HTML)
  - [라우터 트랜지션 문서](https://router.vuejs.org/guide/advanced/transitions.html#per-route-transition)
  - [뷰 트랜지션 문서](https://vuejs.org/v2/guide/transitions.html)
- `NewsView.vue`, `JobsView.vue`, `AskView.vue` Design 개선
  ```html
  // NewsView.vue
  <template>
    <div>
        <p v-for="item in this.$store.state.news" :key="item.id">
          <a v-bind:href="item.url">{{ item.title }}</a>
          <small> {{item.time_ago}} by {{item.user}}. </small>
        </p>
    </div>
  </template>

  // JobsView.vue
  <template>
    <div>
        <p v-for="item in this.$store.state.jobs" :key="item.id">
          <a v-bind:href="item.url">{{item.title}}</a>
          <small> {{item.time_ago}} by {{item.domain}}. </small>
        </p>
    </div>
  </template>

  // AskView.vue
  <template>
    <div>
        <p v-for="item in fetchedAsks" :key="item.id">
          <a v-bind:href="item.url">{{ item.title }}</a>
          <small> {{item.time_ago}} by {{item.user}}. </small>
        </p>
    </div>
  </template>
  ```
- **[적용 샘플 코드]** `NewsView` -> `UserView`로 `Dynamic Route`
  ```javascript
  // routes/index.js
  // #0.1 : 다이나믹 라우트를 위한 라우트 정의
  routes: [
      {
          path: '/user/:id',
          component: UserView,
      }
  ]

  // views/UserView.vue
  // #0.2 : store를 사용하기 위하여 호출할 UI에서 dispatch 적용 (결국 store.action 호출)
  created() {
    const userName = this.$route.params.id;
    this.$store.dispatch('FETCH_USERS', userName);
  }

  // api/index.js
  // #0.3 : axios를 사용하여 api 정의
  function fetchUserInfo(userName) {
      return axios.get(`${config.baseUrl}user/${userName}.json`);
  };
  export {
      fetchUserInfo,
  }

  // store/state.js
  // #0.4 : 사용할 state 정의
  export default {
      users: {},
  }

  // store/mutations.js
  // #0.5 : actions <-> state의 값 할당을 위하여 반드시 필요
  export default {
      SET_USERS(state, data) {
          state.users = data;
      }
  }

  // store/actions.js
  // #0.6 : action(method) 정의
  import { fetchUserInfo } from '../api/index.js';
  export default {
    FETCH_USERS({ commit }, name) {
        fetchUserInfo(name)
        .then(({data}) => {
            commit('SET_USERS', data);
        })
        .catch(error => {
            console.log(error);
        })
    },
  }

  // views/UserView.vue
  // #0.7 : UI 디자인
  <div>
      <p>name : {{userInfo.id}}</p>
      <p>karma : {{userInfo.karma}}</p>
      <p>created : {{userInfo.created}}</p>
  </div>
  export default {
    computed: {
      userInfo() {
        return this.$store.state.users;
      }
    }
  }
  ```
- **[적용 샘플 코드]** `AskView` -> `ItemView`로 `Dynamic Route`
  ```javascript
  // routes/index.js
  // #0.1 : 다이나믹 라우트를 위한 라우트 정의
  routes: [
      {
          path: '/item/:id',
          component: ItemView,
      },
  ]

  // views/AskView.vue
  // #0.2 : store를 사용하기 위하여 호출할 UI에서 dispatch 적용 (결국 store.action 호출)
  <router-link v-bind:to="`/item/${item.id}`">{{item.title}}</router-link>

  created() {
    this.$store.dispatch('FETCH_ASK');
  },

  // api/index.js
  // #0.3 : axios를 사용하여 api 정의
  function fetchCommentItem(id) {
      return axios.get(`${config.baseUrl}item/${id}.json`);  
  };

  // store/state.js
  // #0.4 : 사용할 state 정의
  export default {
      item: []
  }

  // store/mutations.js
  // #0.5 : actions <-> state의 값 할당을 위하여 반드시 필요
  SET_ITEM(state, data) {
      state.item = data;
  }

  // store/actions.js
  // #0.6 : action(method) 정의
  FETCH_ITEM({commit}, id) {
      fetchCommentItem(id)
      .then(({data}) => {
          commit('SET_ITEM', data);
      })
      .catch(error => {
          console.log(error);
      })
  },

  // store/getters.js
  // #0.7 : state에 정의한 item을 사용하기 위한 getters 정의
  fetchedItem(state) {
      return state.item;
  }

  // views/UserView.vue
  // #0.7 : UI 디자인
  <template>
    <div>
        <section>
          <div class="user-container">
            <div>
              <i class="fas fa-user-secret"></i>
            </div>
            <div class="user-description">
              <router-link v-bind:to="`/user/${fetchedItem.user}`">
                {{fetchedItem.user}}
              </router-link>
              <div class="time">
                {{fetchedItem.time_ago}}
              </div>
            </div>
          </div>
          <h2>{{fetchedItem.title}}</h2>
        </section>
        <section>
          <div v-html="fetchedItem.content"></div>
        </section>
    </div>
  </template>

  <style scoped>
  .user-container {
    display: flex;
    align-items: center;
    padding: 0.5rem;
  }
  .fa-user-secret {
    font-size: 2.5rem;
  }
  .user-description {
    padding-left: 8px;
  }
  .time {
    font-size: 0.5rem;
  }
  </style>
  ```

### 3.2 Refactoring - List Item Component
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-6.1 refactoring(List Item)`**
- '`NewsView.vue`', '`AskView.vue`', '`JobsView.vue`' *CSS* 디자인 적용
  ```css
  /* app.vue */
  <style>
    body {
      padding: 0;
      margin: 0;
    }
    a {
      color: #34495e;
      text-decoration: none;
    }
    a.router-link-exact-active {
      text-decoration: underline;
    }
    a:hover {
      color: #42b883;
      text-decoration: underline;
    }
  </style>

  /* ???.vue */
  <styl scoped>
  .news-list {
    margin: 0.3rem;
    padding: 0.2rem;
  }
  .post {
    display: flex;
    list-style: none;
    align-items: center;
    border-bottom: 1px solid #eee;
  }
  .points {
    width: 80px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #42b883;
  }
  .news-title {
    margin: 0;
  }
  .link-text {
    color: #828282;
  }
  ```
- Common Component for ListItem
  - `NewsView`, `AskView`, `JobsView`의 반복되는 코드에 대하여 컴포넌트화
  - 반복되는 코드
    - `script`, `style`, `template`
  - *`ListItem.vue`* 이름으로 콤포넌트를 만들고 중복되는 코드 이동
    - 주요 변경 코드
      ```javascript
      // #0.1 routes/index.js
      // 호출한 페이지를 구분하기 위하여 라우터에 'name' 속성을 추가 및 할당 한다.
      {
          path: '/ask',
          name: 'ask',
          component: AskView,
      },

      // #0.2 NewsView.vue, AskView.vue, JobsView.vue
      // 기존의 코드들이 중복됨으로 중복된 코드는 ListItem.vue로 이동하고
      // 나머지는 최소화 한다.
      <template>
        <div>
          <List-Item></List-Item>
        </div>
      </template>

      <script>
      import ListItem from '../components/ListItem.vue'

      export default {
        components: {
          ListItem,
        }
      }
      </script>

      // #0.3 ListItem.vue
      // <Style></Style>영역은 100% 중복 됨으로 그대로 이동한다.
      // template 핵심 키워드
      // 분기문에서 template v-if, v-else와 tag v-if, v-else 사용 (일부 화면에서 구분해야할 코드 존재)
      <template>
        <div class="news-list">
          <li v-for="item in listItems" :key="item.id" class="post">
            <div class="points">
              {{item.points || 0}}
            </div>
            <div>
              <p class="news-title">
                  <template v-if="item.domain">
                      <a v-bind:href="item.url">{{ item.title }}</a>
                  </template>
                  <template v-else>
                      <router-link v-bind:to="`item/${item.id}`">{{item.title}}</router-link>
                  </template>
              </p>
              <small class="link-text">
                  {{item.time_ago}} by 
                  <router-link v-if="item.user" v-bind:to="`/user/${item.user}`">{{item.user}}.</router-link>
                  <a v-else v-bind:href="item.url">{{item.domain}}</a>
              </small>
            </div>
          </li>
        </div>
      </template>

      // #0.4 생성자 func에서는 각각의 dispatch 호출
      // 각각의 state 사용을 위하여 computed에서 listItem func. 정의
      <script>
      export default {
        created() {
          const name = this.$route.name;

          if(name === 'news') {
              this.$store.dispatch('FETCH_NEWS');
          } else if(name === 'ask') {
              this.$store.dispatch('FETCH_ASK');
          } else if(name === 'jobs') {
              this.$store.dispatch('FETCH_JOBS');
          }
        },
        computed: {
            listItems() {
                const name = this.$route.name;
                if(name === 'news') {
                    return this.$store.state.news;
                } else if(name == 'ask') {
                    return this.$store.state.asks;
                } else if(name == 'jobs') {
                    return this.$store.state.jobs;
                }
            }
        }
      }
      </script>
      ```
 
### 3.3 Refactoring - User Profile Component
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-6.2 refactoring(User Profile)`**
- Common Component for User Profile
- `ItemView`, `UserView` 의 반복되는 코드에 대하여 컴포넌트화
- 반복되는 코드
  - `script`, `style`, `template`
- *`UserProfile.vue`* 이름으로 콤포넌트를 만들고 중복되는 코드 이동
  - 주요 변경 코드 #1 (store 이용)
    ```javascript
    // #0.0 상위 콤포넌트 <-> 하위 콤포넌트간 store의 state를 통하여 데이터 전달하는 경우
    //
    // #0.1 UserView.vue
    // 기존의 코드들이 중복됨으로 중복된 코드는 UserView.vue로 이동하고
    // 나머지는 최소화 한다.
    <template>
      <div>
        <User-Profile></User-Profile>
      </div>
    </template>

    <script>
    import UserProfile from '../components/UserProfile.vue';
    export default {
      components: {
        UserProfile,
      },
      created() {
        const userName = this.$route.params.id;
        this.$store.dispatch('FETCH_USERS', userName);
      },
    }
    </script>

    // #0.2 UserProfile.vue
    // <Style></Style>영역은 그대로 이동한다.
    // 핵심 키워드
    //   -. store에서 state를 이용하여 이미 users를 사용하기 때문에 그대로 사용
    <template>
      <div class="user-container">
          <div>
              <i class="fas fa-user-secret"></i>
          </div>
          <div class="user-description">
              <div>
                {{userInfo.id}}
              </div>
              <div class="time">
                  {{userInfo.created}}
              </div>
          </div>
      </div>
    </template>

    <script>
    export default {
      computed: {
        userInfo() {
          return this.$store.state.users;
        }
      },
    }
    </script>
    ```

  - 주요 변경 코드 #2 (props 이용)
    ```javascript
    // #0.0 상위 콤포넌트 <-> 하위 콤포넌트간 props를 이용하여 데이터 전달
    //
    // #0.1 UserView.vue
    // 기존의 코드들이 중복됨으로 중복된 코드는 UserView.vue로 이동하고
    // 나머지는 최소화 한다.
    <template>
      <div>
        <User-Profile v-bind:info="userInfo"></User-Profile>
      </div>
    </template>

    <script>
    import UserProfile from '../components/UserProfile.vue';
    export default {
      components: {
        UserProfile,
      },
      computed: {
        userInfo() {
          return this.$store.state.users;
        }
      },
      created() {
        const userName = this.$route.params.id;
        this.$store.dispatch('FETCH_USERS', userName);
      },
    }
    </script>

    // #0.2 UserProfile.vue
    // <Style></Style>영역은 그대로 이동한다.
    // 핵심 키워드
    //   -. 'props'를 이용하여 상위 콤포넌트로 부터 'info'라는 속성명으로 내려받은 Object 사용
    <template>
      <div class="user-container">
          <div>
              <i class="fas fa-user-secret"></i>
          </div>
          <div class="user-description">
              <div>
                {{info.id}}
              </div>
              <div class="time">
                  {{info.created}}
              </div>
          </div>
      </div>
    </template>

    <script>
    export default {
      props: {
          info: Object
      },
    }
    </script>
    ```
  - store의 state로 접근(computed) vs props로 전달 및 접근
  <img src="../../assets/images/posts/vue-advanced/3.3 data transfer.png" width="90%"/>
  - [Props Validation API 문서](https://vuejs.org/v2/guide/components-props.html#Prop-Validation)
  - *<h3>`UserProfile`에서 props로 전달된 데이터의 속성이 다를 경우 `template`이나 `v-if, v-else`로 분기할 수 있으나, `slot`을 사용하여 UI의 요소를 재활용</h3>*
    ```html
    <!-- UserProfile.vue
    'username, 'time', 'karma' 이름으로 3개의 slot을 정의하고
    하기 콤포넌트를 사용하는 vue에서 slot의 name속성으로 접근하여 직접 태그를 작성 한다. -->
    <template>
        <div class="user-container">
            <div>
                <i class="fas fa-user-secret"></i>
            </div>
            <div class="user-description">
                <slot name="username"></slot>
                <div class="time">
                    <slot name="time"></slot>
                </div>
                <div class="karma">
                    <slot name="karma"></slot>
                </div>
            </div>
        </div>
    </template>

    <!-- UserView.vue
    'username', 'time', 'karma' 3개의 slot에 데이터를 할당하여 태그를 작성한다. -->
    <template>
      <div>
        <User-Profile v-bind:info="userInfo">
          <div slot="username">{{userInfo.id}}</div>
          <template slot="time">{{userInfo.created}}</template>
          <div slot="karma">{{userInfo.karma}}</div>
        </User-Profile>
      </div>
    </template>

    <!-- ItemView.vue
    'username', 'time' 2개의 slot에 데이터를 할당하여 태그를 작성한다. -->
    <template>
      <div>
          <section>
            <User-Profile v-bind:info="fetchedItem">
              <div slot="username">{{fetchedItem.user}}</div>
              <template slot="time">{{fetchedItem.time_ago}}</template>
            </User-Profile>
          </section>
          <section>
            <h2>{{fetchedItem.title}}</h2>
          </section>
          <section>
            <div v-html="fetchedItem.content"></div>
          </section>
      </div>
    </template>
    ```

  - `router-link`에도 `slot`을 추가하여 사용할 수 있음
    ```html
    <router-link slot="username" v-bind:to="`/user/${fetchedItem.user}`">
      {{fetchedItem.user}}
    </router-link>
    ```

### 3.4 Refactoring - Mixin & HOC(High Order Component)
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-6.3 refactoring(Mixin & HOC)`**
- `이벤트 버스`를 활용하여 컴포넌트 재활용
  - `NewsView`, `AskView`, `JobsView`에서 `Spinner`를 사용
  - 각 뷰와 Spinner간의 데이터 전송을 위하여 `이벤트 버스` 활용
  - [프로그램밍적 이벤트 리스너-$on, $once, $off](https://kr.vuejs.org/v2/guide/components-edge-cases.html#%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%A0%81-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A6%AC%EC%8A%A4%EB%84%88)
    ```javascript
    <!-- #0.0 Spinner 콤포넌트 정의
    components > Spinner.vue -->
    <!-- spinner.vue 파일 참고 -->

    <!-- #0.1 테이터 통신용 'bus' 인스턴스 생성
    utils > bus.js -->
    import Vue from 'vue';
    export default new Vue();

    <!-- #0.2 'bus' 인스턴스 참조, $on, $off 
    App.vue -->
    <template>
      <div id="app">
        ...
        <spinner v-bind:loading="loadingStatus"></spinner>
      </div>
    </template>

    <script>
    import bus from './utils/bus.js';

    export default {
      data() {
        return {
          loadingStatus: false,
        };
      },
      methods: {
        startSpinner() {
          this.loadingStatus = true;
        },
        endSpinner() {
          this.loadingStatus = false;
        }
      },
      created() {
        bus.$on('start:spinner', this.startSpinner);
        bus.$on('end:spinner', this.endSpinner);
      },
      beforeDestroy() {
        bus.$off('start:spinner', this.startSpinner);
        bus.$off('end:spinner', this.endSpinner);
      },
    }
    </script>

    <!-- #0.3
    views > NewsView.vue & JobsView.vue & AskView.vue -->
    <script>
    import bus from '../utils/bus.js';

    export default {
      created() {
        bus.$emit('start:spinner');

        setTimeout(() => {
          this.$store.dispatch('FETCH_NEWS')
          .then(() => {
            console.log('fetched');
            bus.$emit('end:spinner');
          })
          .catch((error) => {
            console.log(error);
          });
        }, 2000); //테스트를 위하여 setTimeout 함수를 사용함
      },
    }
    </script>
    ```
  - [HOC(Higher-Order Components)](https://reactjs.org/docs/higher-order-components.html)
    - 콤포넌트를 재사용하기 위한 기술의 패턴
    - `콤포넌트`가 많아 진다면 `깊이`가 깊어지는 현상이 생기고 `복잡도`도 증가
    - `NewsView`, `AskView`, `JobsView`에 존재하는 `created` Function을 재활용(중복을 한개로)하는 컨셉
      ```javascript
      <!-- routes > index.js -->
      {
          path: '/news', 
          name: 'news',
          component: createListView('NewsView'),
      },
      {
          path: '/ask',
          name: 'ask',
          component: createListView('AskView'),
      },
      {
          path: '/jobs',
          name: 'jobs',
          component: createListView('JobsView'),
      },

      <!-- views > ListView.vue -->
      <template>
        <div>
            <list-item></list-item>
        </div>
      </template>

      <script>
      import ListItem from '../components/ListItem.vue';

      export default {
          components: {
              ListItem,
          },
      }
      </script>

      <!-- views > CreateListView.js -->
      import ListView from './ListView.vue';
      import bus from '../utils/bus.js';

      export default function createListView(name) {
          return {
              // 재사용할 인스턴스(컴포넌트) 옵션들 추가 에정
              name: name,
              created() {
                  bus.$emit('start:spinner');
                  setTimeout(() => {
                      this.$store.dispatch('FETCH_LIST', this.$route.name)
                      .then(() => {
                          console.log('fetched');
                          bus.$emit('end:spinner');
                      })
                      .catch((error) => {
                          console.log(error);
                      });
                  }, 2000);
              },
              render(createElement) {
                  return createElement(ListView);
              },
          }
      }

      <!-- api > index.js에 새로운 API function 정의 -->
      <!-- store > actions.js, mutations.js, state.js 파일 적절하게 수정 -->
          ```
          - [Mixin](https://v3.ko.vuejs.org/guide/mixins.html#%E1%84%80%E1%85%B5%E1%84%8E%E1%85%A9)
            - `콤포넌트`의 일부 기능을 재사용하기 위한 방법으로, 객체의 모든 옵션을 포함할 수 있으며 `Mix`하여 사용하는 패턴
          ```javascript
          <!-- mixins > ListMixin.js -->
          import bus from "../utils/bus.js";

          export default {
            created() {
              bus.$emit("start:spinner");
              this.$store
                .dispatch("FETCH_LIST", this.$route.name)
                .then(() => {
                  console.log("fetched");
                  bus.$emit("end:spinner");
                })
                .catch((error) => {
                  console.log(error);
                });
            },
          };

          <!-- views > NewsView.vue -->
          import ListMixin from "../mixins/ListMixin.js";

          export default {
            components: {
              ListItem,
            },
            mixins: [ListMixin],
          };

          <!-- routes > index.js -->
          {
            path: "/news",
            name: "news",
            component: NewsView,
          },
          ```
- HOC & Mixin의 차이점
  <img src="../../assets/images/posts/vue-advanced/3.4 HOC & Mixin.png" width="90%"/>

### 3.5 Refactoring - Call Data & UX
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-6.4 refactoring(Call Data & UX)`**
- [created 라이프 사이클 훅 API 문서](https://vuejs.org/v2/api/#created)
- [네비게이션 가드 블로그 글 링크](https://joshua1988.github.io/web-development/vuejs/vue-router-navigation-guards/)
- [네비게이션 가드 뷰 라우터 공식 문서](https://router.vuejs.org/guide/advanced/navigation-guards.html#global-guards)
- 데이터의 호출 시점
  > * *라우터 네비게이션 가드*<br/>
  >   * 특정 URL로 접근하기 전에 동작을 정의하는 속성(함수)<br/>
  >   * 접근권한, 인증등 체크<br/>
  > * *컴포넌트 라이프 사이클 훅*<br/>
  >   * created : (컴포넌트가 생성)되자마자 호출되는 함수<br/>
  >   * `HOC`, `Mixin`에서 구현한 경우(상위 참고)
- `Spinner` 개선
  ```javascript
  <!-- store > actions.js
  'Response' 오브젝트를 반환(Return)해 호출한 함수의 'Then'처리를 한다. -->
  FETCH_LIST({ commit }, pageName) {
    return fetchList(pageName)
      .then(({ data }) => {
        console.log(4);
        commit("SET_LIST", data);
      })
      .catch((error) => {
        console.log(error);
      });
  },
  ```
- `라우터 네비게이션 가드`를 활용한 데이터 호출
  ```javascript
  <!-- routes > index.js -->
  <!-- $store, $route만 해당 인스턴스의 객체로 접근하여 사용하고 반드시 next()로 마무리 -->
  {
    path: "/news",
    name: "news",
    component: NewsView,
    beforeEnter: (to, from, next) => {
      bus.$emit("start:spinner");
      store.dispatch("FETCH_LIST", to.name)
      .then(() => {
        bus.$emit("end:spinner");
        next();
      })
      .catch((error) => {
        console.log(error);
      });
    },
  },
  ```
  - `bus.$emit("end:spinner")`가 `routes.index.js`에서 실행하면 잔재가 남아있음으로 `mounted(){}`로 이동한다.
  - `NewView.vue`, `JobsView.vue`, `AskView.vue`에 중복해서 사용한 `mouted(){}`를 `ListMixin.js`로 이동하여 콤포넌트를 재활용 한다.
  - `UX`관점으로 `라우터 네비게이션 가드` 또는 `컴포넌트 라이프 사이클 훅`중 적절하게 사용 필요

### 3.6 Refactoring - Async & Await
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-6.5 refactoring(Async & Await)`**
- [자바스크립트 async와 await](https://joshua1988.github.io/web-development/javascript/js-async-await/)
- <h2>`자바스크립트 비동기 처리 패턴`</h2>
  
  - <img src="../../assets/images/posts/vue-advanced/3.6 javascript 비동기처리.png" width="50%"/>
 
  - 순수 자바스크립의 경우 `id`를 받아오기 위한 함수 호출 즉시 다음 라인의 `john` 비교 구문으로 넘어 간다. 
- `Async` & `Await`
  - `promise`와 `callback`을 사용하여 동기처리가 가능하지만, 단점들을 보완하여 사용하기 쉽고 직관적으로 `동기(절차)적`으로 코드 작성이 가능
    ```javascript
    <!-- 기본 문법 : 반드시 함수앞에 'async'와 비동기 함수 앞에 'await'가 필요 -->
    async function fetchData() {
      await getUserList();
    }
    ```
  - <img src="../../assets/images/posts/vue-advanced/3.6 async_await_1.png" width="50%"/>
  - `promise` vs `async & await` 사용 샘플
    - `App.vue`에서 `loginUser` 함수를 호출하는 버튼 생성하고 REST api 호출후 데이터 바인딩
      ```html
      <template>
        <div>
          <button @click="loginUser1">login</button>
          <h1>List</h1>
          <ul>
            <li v-for="item in items" v-bind:key="item.id">{{ item }}</li>
          </ul>
        </div>
      </template>
      ```
    - 기본 `vue` 파일 정의
      ```javascript
      <script>
      import axios from "axios";

      export default {
        data() {
          return {
            items: [],
          };
        },
      ```
    - `loginUser` 함수 정의 : `promise`, `then`, `catch`를 사용
      ```javascript
      methods: {
          <!-- promise를 사용하여 then, catch로 구현 -->
          loginUser() {
            axios
              .get("https://jsonplaceholder.typicode.com/users/1")
              .then((response) => {
                if (response.data.id === 1) {
                  console.log("사용자 인증되었습니다.");
                  axios
                    .get("https://jsonplaceholder.typicode.com/todos")
                    .then((response) => {
                      this.items = response.data;
                    });
                }
              })
              .catch((error) => console.log(error));
          },
        },
      };
      ```
    - `loginUser1` 함수 정의 : `async`, `await` 를 사용
      ```javascript
        methods: {
          <!-- async, await를 사용하여 구현 -->
          async loginUser1() {
            var response = await axios.get(
              "https://jsonplaceholder.typicode.com/users/1"
            );
            if (response.data.id === 1) {
              console.log("사용자 인증되었습니다.");
              var list = await axios.get(
                "https://jsonplaceholder.typicode.com/todos"
              );
              this.items = list.data;
            }
          },
        };
      ```
    - `Exception` 처리
      ```javascript
      async loginUser1() {
          try {
            <!-- 상동 -->
          } catch (error) {
            handlerException(error);
          }
        },

      <!-- utils > handler.js -->
      export function handlerException(status) {

      }
      ```

## 4. Application Advancement

### 4.1 External Library - Chart
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-7.1 advancement(chart)`**
- 참조 싸이트
  - [Chart.js 공식 문서](https://www.chartjs.org/docs/latest/)
  - [State of JS 2018 사이트](https://2018.stateofjs.com/front-end-frameworks/overview/)
  - [Getting Started](https://www.chartjs.org/docs/latest/getting-started/)
  - [Vue.js 플러그인 문서](https://vuejs.org/v2/guide/plugins.html#ad)
- 외부 라이브러리 모듈화
  - `Vue.js` 관련 라이브러리가 없을 경우는 일반 라이브러리와 `결합`할 수 있어야 함
  - 일반적으로 일반 라이브러리에는 `Chart`, `DatePicker`, `Table`, `Spinner` 등이 존재
- `chart-lib` Vue.js Project 생성 순서
  ```cmd
  <!-- vue create = vue init + npm i 합쳐 짐 -->
  vue create chart-lib

  <!-- chart.js 설치 @2는 버전을 의미 -->
  npm i chart.js@2
  ```
- `error  'myChart' is assigned a value but never used  no-unused-vars` 에러 발생시 `console.log(myChart)`만 추가해줘도 문제 없음
- `eslint` validation 제거 설정 필요[Disallow Unused Variables (no-unused-vars)](https://eslint.org/docs/rules/no-unused-vars)
- Chart.js 사용 샘플
  ```javascript
  <!-- #0.1 챠트 라이브러리 npm으로 설치
  npm i chart.js or npm i chart.js@2 -->

  <!-- #0.2 설치된 chart App.vue에서 import
  import Chart from "chart.js"; -->

  <!-- #0.3 자비스크립트 버전의 코드중 DOM 객체에 접근하는 코드가 존재하여 mounted() 라이프 사이클 훅에 추가 -->
  <canvas id="myChart" width="400" height="400"></canvas>
  mounted() {
    <!-- https://www.chartjs.org/docs/latest/getting-started/usage.html -->
  }

  <!-- #0.4 Chart 컴포넌트화
  BarChart.vue, LineChart.vue를 생성하여 각각 하기와 같으 코드 추가 -->
  <canvas id="barChart"></canvas>
  <script>
  import Chart from "chart.js";
  export default {
  mounted() {
    var ctx = document.getElementById("barChart").getContext("2d");
    <!-- ... -->
  }
  <!-- $refs.명칭을 사용하여 변경 -->
  <canvas ref="barChart" id="barChart"></canvas>
  var ctx = this.$refs.barChart.getContext("2d");

  <!-- App.vue에서 하기와 같이 생성한 BarChar.vue, LineChart.vue를 Import 후 사용 -->
  <template>
    <div>
      <bar-chart></bar-chart>
      <line-chart></line-chart>
    </div>
  </template>

  <script>
  import BarChart from "./components/BarChart.vue";
  import LineChart from "./components/LineChart.vue";

  export default {
    components: {
      BarChart,
      LineChart,
    },
  };
  </script>

  <!-- #0.5 컴포넌트 Plugin화 -->
  <!-- plugins > ChartPlugin.js 를 아래와 같이 정의 한다. -->
  import Chart from "chart.js";
  export default {
    install(Vue) {
      Vue.prototype.$_Chart = Chart;
    },
  };
  <!-- main.js에서 정의한 plugin을 사용하기 위하여 인스턴스 등록 한다. -->
  import ChartPlugin from "./plugins/ChartPlugin.js";
  Vue.use(ChartPlugin);
  <!-- BarChart.vue, LineChart.vue에서 'chart import'를 제거하고 바로 $_Chart로 접근한다. -->
  var myChart = new this.$_Chart(...)

  #0.6 컴포넌트 통신을 통한 컴포넌트 기능 결합

  ```
- 컴포넌트 통신을 통한 기능 결합
  - 좌측(붉은색 라인)
    - App.vue
      - `axios`를 통하여 획득한 데이터를 `props`를 통하여 하위 콤포넌트인 `BarChar`로 내려 보내며, 해당 `BarChar`에서는 `datasets`로 사용
  - 우측(노랑색 라인)
    - BarChart.vue
      - `BarChar`에서 발생한 특정 이벤트(onclick)를 통하여 `emit`으로 상위 콤포넌트인 `App.vue`로 데이터를 전달하고 상위 콤포넌트인 `App.vue`에서 특정 메서드를 호출
- <img src="../../assets/images/posts/vue-advanced/4.1 component data transfer.png" width="100%"/>
- `DOM` 객체에 접근하는 방법 (`refs`의 경우 해당 Component내에서만 라이사이클을 가짐)
  ```javascript
  <template>
    <div ref="VueApp" id="app"></div>
  </template>

  <script>
  <!-- 0.1 Javascript -->
  var divElement = document.getElementById('app');
  var divElement = document.querySelector('#app');

  <!-- 0.2 Jquery -->
  var divElement = $('#app');

  <!-- 0.3 Vue -->
  var divElement = this.$refs.VueApp;
  </script>
  ```

### 4.2 Design Pattern of Component
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-7.2 advancement(design pattern)`**
- Component Design Pattern
  - Common
    - 가장 기본적인 Component 등록 방식
  - Slot
    - 마크업(HTML Tag) 확장이 가능한 방식
  - Controlled
    - 결합력이 높음 방식
  - Renderless
    - 데이터 처리에 효율적인 방식
- Common Component
  - `App.vue`에서 하기의 2개 콤포넌트 등록
    - `App.vue` -> `AppHeader.vue`로 `props`로 `string` 타입의 `title` 전달
    - `App.vue` -> `AppContent.vue`로 `props`로 `Array` 타입의 `items` 전달
    - `AppContent.vue` -> `App.vue`로 `renew` 이름의 `emit` 호출하고 `App.vue`의 `renewItems` 메서드 호출
    - <img src="../../assets/images/posts/vue-advanced/4.2 common_component.png" width="80%"/>
      ```javascript
      <!-- #0.1 App.vue -->
      <template>
        <div>
          <app-header :title="appTitle"></app-header>
          <app-content :items="items" @renew="renewItems"></app-content>
        </div>
      </template>

      <script>
      import AppHeader from './components/AppHeader.vue';
      import AppContent from './components/AppContent.vue';

      export default {
        components: {
          AppHeader,
          AppContent,
        },
        data() {
          return {
            appTitle: 'Common Approach',
            items: [10, 20, 30],
          }
        },
        methods: {
          renewItems() {
            this.items = [40, 50, 60];
          },
        },
      }
      </script>

      <!-- #0.2 AppHeader.vue -->
      <h1>{{ title }}</h1>

      <script>
      export default {
        props: {
          title: String,
        },
      };
      </script>

      <!-- #0.3 AppContent.vue -->
      <li v-for="item in items" v-bind:key="item">
        {{ item }}
      </li>
      <button @click="$emit('renew')">renew items</button>

      <script>
      export default {
        props: {
          items: {
            type: Array,
            required: true,
          },
        },
      };
      </script>
      ```
- Slot Component
  - `App.vue`에서 `Item.vue` 콤포넌트 등록
  - `Item`은 `slot` 태그로 정의되어 있으며, 마크업 확장이 가능(`style`도 가능)
  - <img src="../../assets/images/posts/vue-advanced/4.2 slot.png" width="80%"/>
  
    ```javascript
    <!-- App.vue -->
    <template>
      <div>
        <ul>
          <item> 아이템 1 </item>
          <item> 
            아이템 2 
            <button>click me</button> 
          </item>
          <item>
            <div>아이템 3</div>
            <img src="./assets/endgame.png" />
          </item>
          <item>
            <div style="color: hotpink; font-size: 40px">
              아이템 4
            </div>
          </item>
        </ul>
      </div>
    </template>

    <script>
    import Item from "./Item.vue";

    export default {
      components: {
        Item,
      },
    };
    </script>

    <!-- Item.vue -->
    <template>
      <li>
        <slot>
          <!-- NOTE: 등록하는 곳에서 정의할 화면 영역 -->
        </slot>
      </li>
    </template>
    ```
- Controlled Component
  - 하위 콤포넌트 `CheckBox.vue`에서 `v-model`을 사용해서 체크/언체크 할 때마다 `props` 때문에 오류가 발생
  - <img src="../../assets/images/posts/vue-advanced/4.2 controlled component1.png" width="90%"/>
  - `v-model`은 `input` 이벤트와 `value`값으로 이루어져 내부에서 동작
  - 하위 콤포넌트에서 관리되는 데이터가 상위에서 관리 됨
  - 즉, 받을때는 `@input`, 올려줄때는 `:value`를 사용
  - <img src="../../assets/images/posts/vue-advanced/4.2 controlled component2.png" width="90%"/>
  
- Renderless Component
  - 템플릿이 없이 스크립트만 있다.
  - 표현을하지 않는 콤포넌트(데이터 프로바이더에 대해서 알아본다)
  - [Render Function API 문서 링크](https://vuejs.org/v2/guide/render-function.html#ad)
  - render() 함수
    - 렌더는 콤포넌트를 그릴때 발생하는 함수이다.
    - 등록한 콤포넌트에서만 사용(노출된) 할 수 있다.
  - render() function sample
    ```javascript
    <!-- #0.1 일반적인 Vue 인스턴스 사용 -->
    <div id="app">
      {{message}}
    </div>
    <script>
      new Vue({
        el: '#app',
        data: {
          message: "Hello Vue",
        },
      })
    </script>

    <!-- #0.2 template 사용 -->
    <div id="app">
    </div>
    <script>
      new Vue({
        el: '#app',
        data: {
          message: "Hello Vue",
        },
        template: '<p>{{message}}</p>',
      })
    </script>

    <!-- #0.3 render function 사용 -->
    <div id="app">
    </div>
    <script>
      new Vue({
        el: '#app',
        data: {
          message: "Hello Vue",
        },
        render: function(createElement) {
          //return createElement('태그이름', '태그속성', '하위태그내용');
          return createElement('p', this.message);
        }
      })
    </script>
    ```
    ```javascript
    <!-- main.js에서 Vue 인스턴스 생성시 사용하는 render function 샘플 -->
    new Vue({
      render: h => h(App),
      // 1
      render: function(createElement) {
        return createElement(App);
      },
      // 2
      render: function(h) {
        return h(App);
      },
      // 3
      render: (h) => {
        return h(App);
      },
      // 4
      render: h => h(App),
    }).$mount('#app')
    ```
  - Renderless Component Sample
    - `App.vue`
      - `FetchData` 콤포넌트와 `App`사이 `slot-scope`를 사용
      - `render()` 함수를 사용
      ```javascript
      <template>
        <div>
          <fetch-data url="https://jsonplaceholder.typicode.com/users/1">
            <div slot-scope="{ response, loading }">
              <div v-if="!loading">
                <p>name: {{ response.name }}</p>
                <p>email: {{ response.email }}</p>
              </div>
              <div v-if="loading">Loading...</div>
            </div>
          </fetch-data>
        </div>
      </template>

      <script>
      import FetchData from "./components/FetchData.vue";
      export default {
        components: {
          FetchData,
        },
      };
      </script>
      ```
    - `FetchData.vue`
      ```javascript
      <script>
      import axios from "axios";

      export default {
        props: ["url"],
        data() {
          return {
            response: null,
            loading: true,
          };
        },
        created() {
          axios
            .get(this.url)
            .then((response) => {
              this.response = response.data;
              this.loading = false;
            })
            .catch((error) => {
              alert("[ERROR] fetching the data", error);
              console.log(error);
            });
        },
        render() {
          return this.$scopedSlots.default({
            response: this.response,
            loading: this.loading,
          });
        },
      };
      </script>
      ```

### 4.3 Configuration the Service Distribution Environment
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-advanced-7.3 advancement(Service Distribution)`**
- `npm run build`
- CLI로 생성한 프로젝트를 서비스에 배포하려면 제일 먼저 위 명령어를 실행해야 함. 실행하고 나면 아래와 같이 호스팅할 수 있는 형태의 HTML, CSS, javascript, 이미지등의 파일이 생성됨, 이렇게 생성된 자원을 빌드된 자원이라고 부름
- [Netlify 공식 사이트 주소](https://www.netlify.com/)
- <img src="../../assets/images/posts/vue-advanced/4.3 npm_run_build.png" width="90%"/>
- Netlify 초기 설정
  - <img src="../../assets/images/posts/vue-advanced/4.3 netlify configuration.png" width="100%"/>
- Base 디렉토리 설정 및 배포 확인
  - <img src="../../assets/images/posts/vue-advanced/4.3 base configuration.png" width="100%"/>
- Env 환경 변수 파일을 이용한 옵션 변경 방법
  - [Vue CLI 배포 설명 페이지 링크](https://cli.vuejs.org/guide/deployment.html#netlify)
  - [배포할 서버에 맞는 설정이 필요](https://cli.vuejs.org/guide/deployment.html#platform-guides)
  - <img src="../../assets/images/posts/vue-advanced/4.3 env configuration.png" width="100%"/>

### 5. 출처

  * [인프런](https://www.inflearn.com/course/vue-js/dashboard)
