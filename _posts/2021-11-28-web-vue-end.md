---
title:  "Vue End"
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
 
date: 2021-11-28
last_modified_at: 2021-11-28
---

<img src="../../assets/images/posts/vue-end/vue-advanced.png" width="80%"/>

## 1. Study Agenda
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-1.init`**
- summary
  - 강좌에서 개발할 웹어플리케이션에 대해서 확인하고 일반적인 웹개발 절차와 API 문서에 대해서 알아본다.
### 1.1 Introduce Application
  - `회원가입`, `로그인`, `CRUD`가 발생하는 기본적인 웹어플리케이션
### 1.2 Procedure of Front-End Development
- 웹 개발 절차
  - 요구사항 > 서비스 기획 > UI, UX 상세 설계 > GUI 디자인 > 퍼블리싱 > Back-End API 개발 > Front-End 개발 > QA
- Front-End 개발자의 역할
  - Client UI에 대한 코드 작성
  - 기획, 디자인, 퍼블리싱, Back-End 개발자와 소통
### 1.3 Document of API
- [Swagger UI](https://swagger.io/)
  - [Swagger](https://ko.wikipedia.org/wiki/%EC%8A%A4%EC%9B%A8%EA%B1%B0_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4))는 개발자가 RESTfull API를 설계, 빌드, 문서화, 소비하는 일을 도와주는 오픈소스 소프트웨어 프레임워크

## 2. Configuration of Development Environment
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-2.environment`**
- summary
  - 개발환경 구성에 대해서 알아본다(깃허브, 필수 설치 프로그램, )
### 2.1 개발 환경(Tools)
  - [Chrome](https://www.google.com/intl/ko/chrome/), [Git](https://git-scm.com/downloads), [Visual Studio Code](https://code.visualstudio.com/), [Node.js LTS 버전(v10.x 이상)](https://nodejs.org/ko/), [Vue.js Dev Tools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - Github
    - [개발 소스(Front-End) - Source](https://github.com/joshua1988/vue-til), [API(Back-End) - Source](https://github.com/joshua1988/vue-til-server)
    - `vue-til-server`의 경우 `github`의 `root`에 존재하는 `vue-til-server-master.zip` 다운받아 사용
  - VS Code Plugin
    - 색 테마 : [Night Owl](https://marketplace.visualstudio.com/items?itemName=sdras.night-owl)
    - 파일 아이콘 테마 : [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
    - 뷰 확장 플러그인 : [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
    - 뷰 코드 스니펫 : [Vue VSCode Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
    - 문법 검사 : [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint), [TSLint](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)
    - 실습 환경 보조 : [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
    - 기타
      - [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode), [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense), [Project Manager](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager), [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css), [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag), [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens), [Atom Keymap](https://marketplace.visualstudio.com/items?itemName=ms-vscode.atom-keybindings), [Jetbrains IDE Keymap](https://marketplace.visualstudio.com/items?itemName=isudox.vscode-jetbrains-keybindings) 등

### 2.2 개발 환경 (Visual Studio Code Gitbash Terminal)
- [git bash](https://git-scm.com/downloads)는 Windows에서도 Linux 명령어를 사용할 수 있는 환경
- Visual Studio Code에서도 `gitbash` 터미널을 사용할 수 있다.(본 강좌에서는 사용해야 함)
- 기존의 `terminal.integrated.shell.windows`에 대해서 VSCode 업데이트 됨에 사용할 수 없음([참고](https://code.visualstudio.com/updates/v1_56))
- `Visual Studio Code` > `ctrl + ,` > `terminal.integrated.shell.windows` > `setting.json` open > 하기의 코드 추가
```json
"terminal.integrated.profiles.windows": {
    "GitBash": {
        // 일반적으로 : "C:\\Git\\bin\\bash.exe"
        "path":["사용자별 git 설치 경로\\bash.exe"],
        "icon":"terminal-bash"
    },

    "PowerShell": {
        "source": "PowerShell",
        "icon": "terminal-powershell"
    },
    "Command Prompt": {
        "path": [
            "${env:windir}\\Sysnative\\cmd.exe",
            "${env:windir}\\System32\\cmd.exe"
        ],
        "args": [],
        "icon": "terminal-cmd"
    },
},
// "GitBash"로 설정하면 "Bash"가 기본으로 설정 됨
"terminal.integrated.defaultProfile.windows": "Command Prompt",
```

### 2.3 개발 환경(Node js)
- Node 버전 확인 및 업그레이드 & 다운그레이드
  - 본 강좌의 소스는 `node` 버전이 `v10.16.3`으로 진행해야 함
  - 특정 버전의 Node를 설치하는 방법은 2가지
    - *원하는 LTS 버전을 찾아 해당 OS의 실행 파일로 설치 (GUI로 사용)*
    - *NVM을 사용하여 특정 버전 설치 사용등 (Command Line으로 사용)*
  ```command
  $ node -v
  v14.8.1
  ```
  - [Node js - v10.16.3](https://nodejs.org/download/release/v10.16.3/)에서 OS 버전에 맞는 파일을 다운로드 받아 설치 가능
- NVM(Node Version Manager)
  - NVM을 이용하여 `nodejs` 특정 버전을 설치, 업그레이드 및 다운그레이드 가능
  - [Node js](https://nodejs.org/ko/)
  - [NVM Github](https://github.com/nvm-sh/nvm)
  - `NVM` 설치
    - [NVM 설치 및 버전 변경 절차 문서](https://github.com/joshua1988/vue-til-server#nvm-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EB%B2%84%EC%A0%84-%EB%B3%80%EA%B2%BD-%EB%B0%A9%EB%B2%95)
    - `VSCode` > 터미널을 `Bash`로 열고 하기 명령어 입력
    ```command
    $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
    ```
  - NVM 명령어 등록
    - `VSCode` > 터미널을 `Bash`로 열고 하기 명령어 입력
    ```command
    $ vi ~/.bashrc
    
    // i : 쓰기모드 진입
    export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
    // esc : 쓰기모드 해지
    // :wq : 저장하고 종료 (:q : 저장하지 않고 종료)
    ```
    - `bash` 터미널에서 하기 명령어를 입력하여 정상적으로 `NVM`이 설치 및 명령어가 적용되었는지 확인
    ```command
    $ nvm --version
    0.39.0
    ```
    - 노드 버전을 그냥 전환하고 싶다면  `nvm use 버전 이름` 사용
    - [nvm 노드 버전 설치 가이드](https://www.inflearn.com/questions/281892)
    - `node` 버전 `10.16.3` 설치
    ```command
    $ nvm install 10.16.3

    Downloading and installing node v10.16.3...
    Downloading https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip...
    ################################# 100.0% 
    Computing checksum with sha256sum
    Checksums matched!
    Now using node v10.16.3 (npm v6.9.0)
    Creating default alias: default -> 10.16.3 (-> v10.16.3)

    $ node -v
    v10.16.3
    ```
    - `vue-til-server > package.json` 파일내 패키지 설치를 위한 명령어 실행
    ```command
    $ npm i
    ```
    - `npm run dev`로 서버 실행
    ```command
    $ npm run dev

    ...중략...

    VUE TIL SERVER IS RUNNING ON 3000
    // '3000'에 대한 포트를 사용중이면 하기에서 변경 가능
    // src > app.js > port 번호 수정
    ```
    - `http://localhost:3000/api/docs`로 접속하여 API 서버 확인
### 2.4 개발 환경(MongoDB)
- [MongoDB Site](https://www.mongodb.com/cloud)
- `src > app.js`의 `const db`에서 하기의 생성된 DB를 연결
- <img src="../../assets/images/posts/vue-end/2.4 MongoDB.png" width="100%"/>
- `bash` command > `npm run dev` > Server 기동 > `http://localhost:3000/api/docs` 접속 > /signup API Test
- <img src="../../assets/images/posts/vue-end/2.4 API Test.png" width="100%"/>
### 2.5 개발 환경(Swagger UI API)
- `Node js`로 작서된 `Back-End API` 코드를 `Front-End` 개발자와 `커뮤니케이션`하기 위한 API UI
- `RESTfull API`를 직접 테스트 할 수 있는 API UI
### 2.6 개발 환경(프로젝트 구성 - 프로젝트 생성, ESLint & Prettier)
- [웹팩 데브 서버 설명 글](https://joshua1988.github.io/webpack-guide/devtools/webpack-dev-server.html)
- [Vue.js 개발 생산성을 높여주는 도구 3가지](https://joshua1988.github.io/web-development/vuejs/boost-productivity/)
- `vue --version` 으로 vue/cli 버전 확인
- `vue create vue-til`으로 프로젝트 생성 (Manual로 선택하며, 하기의 이미지 참고)
  - <img src="../../assets/images/posts/vue-end/2.6 vue cli.png" width="100%"/>
- [`ESLint`](https://eslint.org/) 구문 오류([ESLint 란?](https://en.wikipedia.org/wiki/ESLint))
  - <img src="../../assets/images/posts/vue-end/2.6 eslint (1).png" width="100%"/>
  - 해결 방법
    - `vue.config.js` 파일 생성하고 하기와 같은 코드 삽입
    - `빌드 오류`는 발생하나 `오버레이` 안됨
    ```javascript
    module.exports = {
      devServer: {
        overlay: false,
      },
    };
    ```
  - ESLint 설정 파일 설정 방법
    - root > `.eslintrc.js` 파일에 하기와 같이 개발자 커스텀 설정 가능
  ```javascript
  rules: {
    "no-console": "error", // 정상을 위하여 "off"로 설정 필요
    // "no-console": process.env.NODE_ENV === "production" ? "warn" : "off",
    // "no-debugger": process.env.NODE_ENV === "production" ? "warn" : "off",
  },
  ```
    - `console` 명령서 사용시 `error` 출력으로 설정함으로 하기와 같이 오류 발생
    - <img src="../../assets/images/posts/vue-end/2.6 eslint (2).png" width="100%"/>
  - ESLint 구문 오류시 해당 구문에 `빨간줄`이 생기지 않을 경우
    - VSCode `설정` > `settings.json`에 하기 코드 추가
    ```json
    "editor.codeActionsOnSave": {"source.fixAll.eslint": true},
    "eslint.workingDirectories": [{"mode": "auto"}],
    ```
- [Prettier](https://prettier.io/) (일관성 있는 코드 포맷을 위한 웹팩)
  - 하기의 이미지처럼 `prettier` 구문을 적용하면 코드에 붉은색 라인이 생기며 빌드 오류 발생
  - <img src="../../assets/images/posts/vue-end/2.6 prettier (1).png" width="100%"/>
  - 해결 방법
    - `설정`의 `eslint: validate` > `settings.json` 파일에서 하기 축
    - <img src="../../assets/images/posts/vue-end/2.6 eslint settings.png" width="100%"/>
    ```json
    "editor.codeActionsOnSave": {
          "source.fixAll.eslint": true
      },
      "eslint.workingDirectories": [
          {
              "mode": "auto"
          }
      ],
      // ESLint
      "eslint.validate":[
          "vue", 
          "javascript", 
          "javascriptreact", 
          "typescript", 
          "typescriptreact"
      ],
      // don't format on save
      "editor.formatOnSave": false,
    ```
    - `prettier` 확장 프로그램에서 `사용안함(작업영역)` 설정
    - `설정`의 `Format on Save` 체크 해지
    - <img src="../../assets/images/posts/vue-end/2.6 prettier settings.png" width="100%"/>
### 2.7 개발 환경(기타)
- 파일의 절대 경로를 사용해야 하는 이유
  - 상대 경로를 이용한 컴포넌트 `import`는 depth가 많아 질수록 folder가 많아 질수록 복잡해 짐
  - 이러한 상대 경로에서의 복잡함을 없애기 위해서 VSCode 설정을 활용한 절대 경로 사용
  - [jsconfig.json 파일 링크(Vue TIL 리포지토리)](https://github.com/joshua1988/vue-til/blob/complete/jsconfig.json)
  - [VSCode의 jsconfig.json 파일 설명 글](https://code.visualstudio.com/docs/languages/jsconfig)
  - <img src="../../assets/images/posts/vue-end/2.6 Absolute Path (1).png" width="100%"/>
  - <img src="../../assets/images/posts/vue-end/2.6 Absolute Path (2).png" width="100%"/>
- Vue.js 공식팀에서 권고하는 스타일 가이드 준수
  - Priotiry A : Essential, Priority B : Strongly Recommened
  - [Vue.js 스타일 가이드 문서](https://kr.vuejs.org/v2/style-guide/index.html)

## 3. Router & Design of Component
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-3.router_component`**
- summary
  - 로그인, 회원가입 UI 개발
- [수업 깃헙 리포지토리 안내](https://github.com/joshua1988/vue-til)
```command
// vue-til 소스를 최초에 설치할 경우
$ git clone https://github.com/joshua1988/vue-til
$ git checkout 1_setup
$ npm i
```
- [Window History API](https://developer.mozilla.org/en-US/docs/Web/API/Window/history)
- [웹팩 코드 스플리팅 문서](https://webpack.js.org/guides/code-splitting/)
- [Vue.js 다이나믹 임포트 문서](https://vuejs.org/v2/guide/components-dynamic-async.html#ad)
### 3.1 Router
- LoginPage, SignupPage 생성 및 라우터 설정
- router 설치
```command
$ npm i vue-router
```
- Code Splitting(코드 스플리팅)
  - 최초 로딩시 리소스를 최소화하여 가져오고 이후 뷰페이지 호출시 리소스를 로딩함
  - <img src="../../assets/images/posts/vue-end/3.1 code spliting.png" width="100%"/>
  ```javascript
  export default new VueRouter({
	routes: [
      {
        path: '/login',
        component: () => import('@/views/LoginPage.vue'),
      },
      {
        path: '/signup',
        component: () => import('@/views/SignupPage.vue'),
      },
    ],
  });
  ```
- [뷰 라우터 오픈 소스](https://github.com/vuejs/vue-router)
- [뷰 라우터 History Mode 주의 사항 문서](https://router.vuejs.org/guide/essentials/history-mode.html)
  - `history` 모드의 경우 URL에 `#`이 없이 나타난다.(서버가 새로운 페이지로 인식하지 못 함)
  - 서버가 새로운 페이지로 인식을 못 함으로 서버에 설정이 필요함.
- fallback router
  - 지정된 경로가 아닌 경우를 대비
```javascript
export default new VueRouter({
	mode: 'history',
	routes: [
		{
			path: '/login',
			component: () => import('@/views/LoginPage.vue'),
		},
		{
			path: '/signup',
			component: () => import('@/views/SignupPage.vue'),
		},
		{
			path: '*',
			component: () => import('@/views/NotFoundPage.vue'),
		},
	],
});
```

## 4. Development of Member Register
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-4.dev_member`**
- summary
  - 회원 가입을 위한 `가입 폼 양식`, `데이터 바인딩`, `이벤트 연결`, `API`에 대해서 개발
- [타입스크립트 핸드북](https://joshua1988.github.io/ts/)
- [async await 정리글](https://joshua1988.github.io/web-development/javascript/js-async-await/)
- [ES6 템플릿 리터럴(백틱) 정리글](https://joshua1988.github.io/es6-online-book/template-literal.html)
- [ES6 Destructuring 정리글](https://joshua1988.github.io/es6-online-book/destructuring.html)
- <img src="../../assets/images/posts/vue-end/4.1 member register form.png" width="100%"/>
- `SignupPage`에서 `SignupForm` 콤포넌트사용하며, `SignupPage`에서 `Axios` 사용

## 5. Configuration of Project
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-5.configure`**
- summary
  - `axios` 사용 `api` 콤포넌트에서 환경 설정 값을 사용
- 참고 자료
  - [axios create() 문서](https://github.com/axios/axios#axioscreateconfig)
  - [웹팩 DefinePlugin 문서](https://webpack.js.org/plugins/define-plugin/)
  - [Vue CLI env 파일 규칙 문서](https://cli.vuejs.org/guide/mode-and-env.html#modes-and-environment-variables)
- <img src="../../assets/images/posts/vue-end/5.1 configuration.png" width="100%"/>
- `VUE_APP` 접두사가 붙으면 코드에서 자동 인식

## 6. Development of Login
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-6.dev_login`**
- summary
  - `로그인 양식`, `API`, `Validation` & `Exception` 기능 구현
- [Email Validation 정규 표현식 코드](https://stackoverflow.com/questions/46155/how-to-validate-an-email-address-in-javascript)
- 로그인 계정
  - ID : a@a.com
  - PWD : 1234
- <img src="../../assets/images/posts/vue-end/6.1 login component.png" width="100%"/>

## 7. Store & Login State Management
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-7.store_state`**
- summary
  - `Style`, `Main Page`
### 7.1 Style
  - css/common.css, css/reset.css
  - App.vue, AppHeader.vue
### 7.2 [뷰 라우터 Programmatic Navigation 문서](https://router.vuejs.org/guide/essentials/navigation.html#programmatic-navigation)
  - `vue router > router-link`를 사용(html 레벨)
  - `vue router > router.push`를 사용(javascript 레벨)
### 7.3 로그인 후 사용자 정보 표시(`store`를 사용)
  - <img src="../../assets/images/posts/vue-end/7.1 vuex-store.png" width="100%"/>
  - [개발용 라이브러리와 배포용 라이브러리 구분하기 문서](https://joshua1988.github.io/webpack-guide/build/npm-module-install.html#npm-%EC%A7%80%EC%97%AD-%EC%84%A4%EC%B9%98-%EC%98%B5%EC%85%98-2%EA%B0%80%EC%A7%80)
    - `npm run build`는 `package.json`의 `dependencies`에 해당하는 라이브러리를 포함하여 빌드
    - `package.json`의 `devDependencies`는 빌드될때 포함되지 않음
  - `Vuex`를 활용하여 `Store`, `State`, `mutations` & `getters`를 활용

## 8. API Authentication by Token
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-8.api_auth_token`**
- summary
  - `API`를 통하여 통신할 경우 `JWT(Json Web Token)`인증을 통하여 통신
- [Json web 토큰 문서](https://jwt.io/)
- [액시오스 인터셉터 문서](https://github.com/axios/axios#interceptors)
  - 인터셉터를 통하여 `axios.create`에서의 `token`값 할당에 대한 초기화 문제를 해결

## 9. Development of Retrieve Note Data
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-9.dev_retrieve`**
- summary
  - `목록 조회` 개발, `style` 적용, `컴포넌트화`, `로딩 상태` & `로딩 스피너` 개발
- `PostItem`에 대하여 컴포넌트화 (MainPage에서 `props`로 컴포넌트로 값 전달)
```javascript
// MainPage.vue
<template>
	<div>
		<div class="main list-container contents">
			<h1 class="page-header">Today I Learned</h1>
			<ul>
				<PostListItem
					v-for="postItem in postItems"
					v-bind:key="postItem._id"
					v-bind:postItem="postItem"
				></PostListItem>
			</ul>
		</div>
	</div>
</template>
export default {
	components: {
		PostListItem,
	},
}

// PostListItem.vue
<template>
	<li>
		<div class="post-title">
			{{ postItem.title }}
		</div>
		<div class="post-contents">
			{{ postItem.contents }}
		</div>
		<div class="post-time">
			{{ postItem.createdAt }}
		</div>
	</li>
</template>

<script>
export default {
	props: {
		postItem: {
			type: Object,
			required: true,
		},
	},
};
</script>
```

## 10. Management of Authentication Value using Browser Storage
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-10.mgmt_auth_browser_storage`**
- summary
  - 로그인한 세션 정보를 위하여 쿠키 사용
### 10.1 Cookie Save
- 쿠키 저장
- <img src="../../assets/images/posts/vue-end/10.1 cookie save 1.png" width="100%"/>
- `store > index.js`의 `state`에서 쿠키값 보존을 위한 코드 추가
```javascript
state: {
		username: getUserFromCookie() || '',
		token: getAuthFromCookie() || '',
	},
```
### 10.2 코드 정리
- async, await를 왜 사용하는지 반드시 인지하고 넘어 가야 함
- 자바스크립트는 기본이 비동기 처리 방식이나 async, await를 사용하여 동기화 처리 필요

## 11. Development of Create Note Data
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-11.dev_create`**
- summary
  - 게시물을 신규 생성하는 UI 개발
- 참고 싸이트
  - [아이오닉 아이콘 사이트](https://ionic.io/ionicons/usage)
- <img src="../../assets/images/posts/vue-end/11.1 create_post.png" width="100%"/>

## 12. Middle Adjustment
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-12.middle_adj`**
- summary
  - [Github Review 참고 파일](https://github.com/LabofDev/vue-til/blob/9_review/review.md)
### 12.1. 개발환경 설정
- 개발 툴 및 필요 프로그램 설치
- API 서버 프로젝트 클론
### 12.2. Vue CLI 프로젝트 생성
- Prettier
- ESLint
- jsconfig
### 12.3. 뷰 라우터 및 컴포넌트 설계
- `<router-link>`
- `<router-view>`
- `mode: history`와 서버 배포시 주의 사항
- 코드 스플리팅 `component: () => import('경로')`
### 12.4. 회원 가입 페이지 개발
- 사용자 폼 처리
- async & await
- axios
- swagger API 문서 보는 방법
### 12.5. 실무 환경 구성
- `axios.create()`
- env 파일 설정 방법
- Vue CLI 버전 3 이상에서의 env 파일 규칙
### 12.6. 로그인 페이지 개발
- 사용자 폼 처리 기능 구현
- async & await 에러 처리 방법
- 사용자 폼 유효성 검사
### 12.7. 로그인 상태 관리
- 뷰엑스를 이용한 사용자 아이디 관리
- `this.$router.push('/main')`
### 12.8. API 인증 처리를 위한 토큰 관리
- JSON Web Token
- `Authorization` 토큰 값으로 API 인증을 받는 방법
- `axios.interceptors`
### 12.9. 학습 노트 데이터 조회
- 학습 노트 목록 표시 기능 구현
- 목록 아이템 컴포넌트화
- 스피너를 이용한 데이터 로딩 상태 표시
### 12.10. 브라우저 저장소를 이용한 인증 값 관리
- 쿠키를 이용한 로그인 인증 값 저장
- actions를 이용한 컴포넌트 로직 정리
### 12.11. 학습 노트 데이터 생성   
- 학습 노트 생성 기능 구현
- 학습 노트 본문 길이 유효성 검사
### 12.12 `13`부터 진행할 내용
- 데이터 성격 별로 API 함수 모듈화
- 학습 노트 삭제 기능
- 날짜 형식 포맷팅 filter
- 라우터 심화
- 프런트엔트 테스트

## 13. API Function Modularity
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-13.api_modularity`**
- summary
  - `API` function의 모듈화로 기능의 성격별로 또는 서브-도메인의 성격별로 분리(모듈화) 진행
  - 추후 시스템이 확장될 경우를 대비하여 처음부터 `확장성`을 고려하여 `API 호출 함수` 모듈화 필요
- Key Sample Code
  - `api > index.js` 파일에서 기능적으로 유사한 함수끼리 모아 분리 모듈화
  - 인스터스를 2개로 구분하는데 `인증전(로그인전)`과 `인증후(로그인후)`
  ```javascript
  import axios from 'axios';
  import { setInterceptors } from './common/interceptors';

  // 엑시오스 초기화 함수 (인증전 즉, 로그인 전)
  function createInstance() {
    return axios.create({
      baseURL: process.env.VUE_APP_API_URL,
    });
  }

  // 액시오스 초기화 함수 (인증후 즉, 로그인 후)
  function createInstanceWithAuth(url) {
    const instance = axios.create({
      baseURL: `${process.env.VUE_APP_API_URL}${url}`,
    });
    return setInterceptors(instance);
  }
  export const instance = createInstance();
  export const posts = createInstanceWithAuth('posts');
  ```
  - `api > auth.js` 로그인 관련 `API function 모듈`
  ```javascript
  // 로그인, 회원 가입, 회원 탈퇴 등을 위한 API
  import { instance } from './index';

  // 회원가입 API
  function registerUser(userData) {
    return instance.post('signup', userData);
  }

  // 로그인 API
  function loginUser(userData) {
    return instance.post('login', userData);
  }

  export { registerUser, loginUser };
  ```
  - `api > posts.js` 게시물 관련 `API function 모듈`
  ```javascript
  // 학습 노트 조작과 관련된 CRUD API 함수
  import { posts } from './index';

  // 학습 노트 데이터를 조회하는 API
  function fetchPosts() {
    return posts.get('/');
  }

  // 학습 노트 데이터를 생성하는 API
  function createPost(postData) {
    return posts.post('/', postData);
  }

  export { fetchPosts, createPost };
  ```

## 14. & 15. Development of Delete Note Data & Modify Note Data
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-14.dev_delete`**
- summary
  - 게시물 삭제 및 수정
  - [Toast Popup](https://github.com/joshua1988/vue-til/blob/complete/src/components/common/ToastPopup.vue)
- 게시물 삭제
  - `API`에 삭제 함수 생성 `PostListItem`에서 `deleteItem` 이벤트 처리
  ```javascript
  async deleteItem() {
			if (confirm('You want to delete it?')) {
				await deletePost(this.postItem._id);
				this.$emit('refresh');
			}
		},
  ```
- 게시물 수정
  - `API`에서 `id`를 인자로 게시물을 조회하는 함수 추가
  - `PostEditPage.vue`와 `PostEditForm.vue`를 생성하여 데이터 변경
- `삭제`와 `수정`후 `push`를 사용하여 `main`으로 이동
```javascript
this.$router.push('/main');
```

## 16. Data Formatting
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-16.data_format`**
- summary
  - 특정 데이터의 `포맷팅` 처리
  - [뷰 필터 안내 문서](https://vuejs.org/v2/guide/filters.html#ad)
- 16.1 `Filter` 함수 사용
  - utils > filters.js 정의
  ```javascript
  export function formatDate(value) {
    const date = new Date(value);
    const year = date.getFullYear();
    let month = date.getMonth() + 1;
    month = month > 9 ? month : `0${month}`;
    const day = date.getDate();
    let hours = date.getHours();
    hours = hours > 9 ? hours : `0${hours}`;
    const minutes = date.getMinutes();
    return `${year}-${month}-${day} ${hours}:${minutes}`;
  }
  ```
  - main.js에 전역으로 사용할 필터 정의
  ```javascript
  //main.js
  import { formatDate } from '@/utils/filters';
  Vue.filter('formatDate', formatDate);
  ```
  - 전역으로 정의한 필터 사용
  ```javascript
  <div class="post-time">
    {{ postItem.createdAt | formatDate }}
    <i class="icon ion-md-create" @click="routeEditPage"></i>
    <i class="icon ion-md-trash" @click="deleteItem"></i>
  </div>
  ```

## 17. Router Advanced
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-17.router_adv`**
- summary
  - 라우터에서 권한 설정
  - Logo 클릭시 `v-bind:on="computed"`를 사용하여 'main' 또는 'login' 분기
  - Logout 클릭시 `cookie(til_auth, til_user)`와 `state의 token` 제거
  - [라우터 네비게이션 가드 문서](https://router.vuejs.org/guide/advanced/navigation-guards.html)
  - [라우터 네비게이션 가드 관련 영상(완벽 가이드 수강 권한 필요)](https://www.inflearn.com/course/vue-js/lecture/17055?tab=curriculum)
- Sample Code
```javascript
//routes > index.js
const router = new VueRouter({
	mode: 'history',
	routes: [
    {
      path: '/post/:id',
      component: () => import('@/views/PostEditPage.vue'),
      meta: { needAuth: true },
    },
  ]
});

router.beforeEach((to, from, next) => {
	if (to.meta.needAuth && !store.getters.isLogin) {
		console.log('인증이 필요합니다.');
		next('/login');
		return;
	}
	next();
});
```

## 18. Introduce of Front-End Testing
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-18.front_end_test`**
- summary
  - [State of JS 2019 - 테스팅](https://2019.stateofjs.com/testing/)
  - [Jest 공식 사이트](https://jestjs.io/)
  - [Jest describe() API 문서](https://jestjs.io/docs/api#describename-fn)
  - [Vue Test Utils 공식 문서](https://vue-test-utils.vuejs.org/guides/)
  - [find() API 문서](https://vue-test-utils.vuejs.org/api/wrapper/#find)
- 18.1 `Jest` 테스트를 위한 환경 설정
  ```javascript
  //`package.json` 설정
    "scripts": {
    "test": "vue-cli-service test:unit --watchAll",
  },
  //--watchAll : 변경즉시 반영 됨
  ```
  ```javascript
  //jest.config.js 설정
  module.exports = {
    preset: '@vue/cli-plugin-unit-jest',
    testMatch: [
      '<rootDir>/src/**/*.spec.(js|jsx|ts|tsx)|**/__tests__/*.(js|jsx|ts|tsx)',
    ],
  };
  ```
  ```command
  // 테스트 실행 명령어
  $npm t
  ```
  ```javacript
  // jest 함수들의 eslint 인식 빨간펜 처리
  // .eslintrc.js
  env: {
    node: true,
    jest: true,
  },
  ```
- 18.2 `Jest` 일반 사항
  - 제일 먼저 `jest.config` 파일의 설정을 참고하며, 설정 파일이 없다면 하기의 기본 설정 폴더를 참고
    - `test > unit > *.spec.js`
  - 일반적으로 `테스트 스크립트` 파일은 테스트 `대상의 인근`에 생성하고 관리
  - 또는 `jest.config.js`파일에서와 같이 `__tests__`와 같이 폴더 생성하여 관리
- 18.3 `Jest Test Code` 작성
  - vuejs test library
  ```javascript
  import { shallowMount } from '@vue/test-utils';
  ```
  - find() function sample
  ```javascript
  import LoginForm from './LoginForm.vue';
  import { shallowMount } from '@vue/test-utils';

  describe('LoginForm.vue', () => {
    test('ID는 이메일 형식이여야 한다.', () => {
      const wrapper = shallowMount(LoginForm);
      const idInput = wrapper.find('#username');
      console.log(idInput.html());
    });
  });
  ```
  - 인스턴스를 생성한 `vue` 페이지의 `computed`에도 접근 가능
  ```javascript
  describe('LoginForm.vue', () => {
    test('ID는 이메일 형식이여야 한다.', () => {
      const wrapper = shallowMount(LoginForm, {
        data() {
          return {
            username: 'test@abc.com',
          };
        },
      });
      const idInput = wrapper.find('#username');
      console.log('InputBox Value ', idInput.element.value);
      console.log(wrapper.vm.isUsernameValid);
    });
  });
  ```
  - `LoginForm.vue`에서 `로그인` 버튼의 활성/비활성화 코드 추가후 테스트 코드 작성
  ```javascript
  // LoginForm.vue
  <button
    :disabled="!isUsernameValid || !password"
    type="submit"
    class="btn"
    v-bind:class="!isUsernameValid || !password ? 'disabled' : null"
  >

  // LoginForm.spec.js
  test('#3. ID와 PWD가 입력되지 않으면 로그인 버튼이 비활성화 된다.', () => {
		const wrapper = shallowMount(LoginForm, {
			data() {
				return {
          // 값이 없으면 통과, 값이 있으면 실패
					username: 'a@a.com',
					password: '1234',
				};
			},
		});
		const button = wrapper.find('button'); // '.btn'
		expect(button.element.disabled).toBeTruthy();
	});
  ```

## 19. End of
- [Github](https://github.com/LabofDev/Vue.git) Branch Name : **`vue-endofvue-19.end`**
- summary
  - 프로젝트 구성 방법
    - ESLint, Prettier
    - env
  - REST API를 이용한 CRUD Application 구현 방법
  - Back-End API 문서 보는 방법 및 Back-End 개발자와 협업할때의 주의 사항
  - axios 인터셉터와 모듈화를 이용한 API 함수 설계
  - Router 페이지 권한 처리
  - Front-End 테스트 방법


## 20. 출처

  * [인프런](https://www.inflearn.com/course/vue-js/dashboard)
