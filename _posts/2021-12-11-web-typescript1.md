---
title:  "TypeScript 기초"
excerpt: "장기효 강사의 타입스크립트 입문 강좌를 수강하며 학습 목적으로 작성된 자료 입니다. 출처는 하단을 참고 바랍니다."
comments: true
header:
  teaser: 

categories:
  - web
tags:
  - [Blog, TypeScript]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2021-12-11
last_modified_at: 2021-12-11
---

<img src="../../assets/images/posts/typescript-1/typescript.png" width="100%"/>

## 1. 오리엔테이션
### 1.1 정의
-. 캡틴 판교의 인프런 강의를 기반으로 학습 자료를 정리

## 2. 소개 와 배경
### 2.1 타입 스크립트란?
- [타입스크립트 공식 문서](https://www.typescriptlang.org/)
- 타입스크립트는 자바스크립트의 슈퍼셋(타입을 부여) 언어입니다. 자바스크립트의 확장된 언어. 
- 타입스크립트는 브라우저에서 실행하려면 파일을 컴파일(complile) 하여야 함.

## 3. 시작하기
### 3.1 환경 준비
- [강의 리포지토리 주소 바로가기](https://github.com/joshua1988/learn-typescript)
- [NVM(Node Version Manager) 깃헙 링크](https://github.com/nvm-sh/nvm)
- [NVM(Node Version Manager) 설치 방법 링크](https://github.com/joshua1988/vue-til-server#nvm-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EB%B2%84%EC%A0%84-%EB%B3%80%EA%B2%BD-%EB%B0%A9%EB%B2%95)
- [팀 개발을 위한 GIt, Github 시작하기 강좌](https://www.inflearn.com/course/%ED%8C%80%EA%B0%9C%EB%B0%9C-%EA%B9%83-%EA%B9%83%ED%97%88%EB%B8%8C?inst=78af1b7b)
- [팀 개발을 위한 Git, GitHub 시작하기](http://www.yes24.com/Product/Goods/85382769?Acode=101)
- [타입스크립트 핸드북](https://joshua1988.github.io/ts/)
- [HTTP 요청 라이브러리 axios](https://github.com/axios/axios)
- [Promise 소개 글](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
- [JSONPlaceHolder 사이트](https://jsonplaceholder.typicode.com/)
- [Jsdoc 문서 안내](https://devdocs.io/jsdoc/)
- [Intellisense 문서](https://code.visualstudio.com/docs/editor/intellisense)
  
### 3.2 타입스크립트를 사용해야 하는 이유

- 개발 단계에서의 문법 및 타입(형) 에러의 사전 방지
  - sample code
  
  ```javascript
  // Jsdoc 문법을 사용하여 함수의 스펙 정의
  /**
  * @typedef {object} Address
  * @property {string} street
  */

  /**
  * @typedef {object} User
  * @property {string} name
  * @property {string} email
  * @property {string} address
  */

  /**
  * @returns {Promise<User>}
  */
  function fetchUser() {
      return axios.get(url);
  }
  fetchUser().then(function(response) {
      console.log(response.address.city); // address에 city가 정의되지 않았다고 소스단에서 확인 가능
  });
  ```
- 코드 가이드 및 자동 완성(Intellisense)
  - sample code
```javascript
// 하기와 같은 경우 sum() 함수에 대해서 a:any, b:any와 같이 형이 없다
function sum(a, b) {
    return a + b;
}
sum(10, 20);
```
```javascript
// typescript
function add(a: number, b: number): number {
    return a + b;
}
add(10, '20');//와 같이 문자열로 지정시 파라메터의 형(type)이 맞지 않아 코드레벨에서 오류 확인
add(10, 20);//정상적인 타입(형)을 사용
```

### 3.3 JavaScript를 TypeScript처럼 사용하는 방법

- jsDoc를 사용하여 `파라메터`에 대해서 정의하고 `//@ts-check` 구문으로 TypeScript 구문 오류 확인
  
```javascript
// @ts-check
/**
 * @param {number} a 첫번째 숫자
 * @param {number} b 두번째 숫자
 * @returns {number}
 */
function sum(a, b) {
    return a + b;
}
var SumResult = sum(10, '20');//'20'에 붉은 라인이 생김
```

### 3.4 TypeScript 시작과 컴파일
- [NPM 무료 강의](https://www.inflearn.com/course/%ED%94%84%EB%9F%B0%ED%8A%B8%EC%97%94%EB%93%9C-%EC%9B%B9%ED%8C%A9/lecture/37370?tab=curriculum)
- [NPM 소개 문서](https://joshua1988.github.io/webpack-guide/build/node-npm.html#npm)
- [npm i typescript -g 명령어 의미](https://joshua1988.github.io/webpack-guide/build/npm-module-install.html#npm-%EC%A0%84%EC%97%AD-%EC%84%A4%EC%B9%98)
- [웹팩 핸드북(문서)](https://joshua1988.github.io/webpack-guide/)
- [프론트엔드 개발자를 위한 웹팩(온라인 강의)](https://www.inflearn.com/course/%ED%94%84%EB%9F%B0%ED%8A%B8%EC%97%94%EB%93%9C-%EC%9B%B9%ED%8C%A9)
- [타입스크립트 설정 파일 옵션(문서)](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
- [플레이그라운드 사이트](https://www.typescriptlang.org/play)
- [바벨 사이트](https://babeljs.io/)
- `TypeScript`는 컴파일러를 이용하여 컴파일해야 한다. 즉, `*.tx` -> `*.js` 컴파일 명령어 및 옵션을 사용하여 컴파일
```javascript
$ node -v // nodejs 버전 확인
$ npm i typescript -g // typecript 설치(-g 옵션으로 글로벌 설치)
$ tsc index.ts // typescript compile
$ node index.js // 컴파일된 index.js 파일 실행
```
- `tsconfig.json` 파일을 사용하여 설정 파일을 생성 및 관리 가능
```javascript
// 참조 : https://www.typescriptlang.org/docs/handbook/tsconfig-json.html
{
    "compilerOptions": {
        "allowJs": true,
        "checkJs": true,
        "noImplicitAny": true
    }
}
```

## 4. 기초 - 변수와 함수 타입
### 4.1 변수와 함수에 대한 참고
- [타입스크립트 변수 타입](https://joshua1988.github.io/ts/guide/basic-types.html)
- [Let & Const 안내 문서](https://joshua1988.github.io/es6-online-book/const-let.html)
- [개발 환경 구성 링크](https://github.com/joshua1988/learn-typescript#%EA%B0%9C%EB%B0%9C-%ED%99%98%EA%B2%BD)
- [타입스크립트 핸드북 - 함수](https://joshua1988.github.io/ts/guide/functions.html)

### 4.2 `const`, `let`

```javascript
// ES6에서 사용하던 변수 선언 방식
// let
// 한번 선언 후 다시 선언할 수 없음
let a = 10;
let a = 20; // Error 발생

// const
// 한번 할당한 값을 재할당 및 변경 할 수 없음
const a = 10;
a = 20; // Error 발생
```
### 4.3 `String`, `Number`, `Boolean`, `Array`, `Tuple`, `Any`, `Void`, `Never`
```javascript
let str: string = 'Hello'; // string
let num: number = 14; // number
let isValid: boolean = false; // boolean
let arr: number[] = [1, 2, 3]; // array
let arr: Array<number> = [1, 2, 3]; // array[type]
let arr: Array<string> = ['one', 'two', 'tree']; // array[type]
let arr: [string, number] = ['one', 1]; // 배열의 길이 고정, 각 요소 타입 지정

enum A = { a = 2, b, c} // 특정 값(상수)들의 집합
let enumA: A = A.b; // b
let enumB: A = A[1]; // b
let enumC: A = A[2]; // a 반환
let enumD: A = A[4]; // c 반환

// Any : 기존의 javascript -> typescript로 migration시 가장 많이 사용
// 모든 타입을 의미 한다.
let str: any = 'Hello';
let str: any = 15;
let arr: any = ['a', 2, true];

// Never : 함수의 끝에 절대로 도달하지 않는다 (무한 루프)
function neverEnd() : never {
    while(true) {}
}
```
### 4.4 블럭의 유효 범위
- `var`의 유효 범위는 함수의 블럭 단위
- `for` 반복문에서의 `var` 유효 범위 (반복문의 변수명에 따라 다름)
  - `let`을 통하여 해결
  ```javascript
  var a = 10;
    for (var a = 0; a < 5; a++) {
        console.log(a); // 0 1 2 3 4 5
    }
    console.log(a); // 6

    var a = 10;
    for (let a = 0; a < 5; a++) {
        console.log(a); // 0 1 2 3 4 5
    }
    console.log(a); // 10
  ```

### 4.5 함수 및 파라메터(옵셔널)

```javascript
function sum(a: number, b: number): number {
    return a + b;
}
sum(10, 20, 30, 40);//30, 40 파라메터로 Error

function sum(a: number, b?: number): number {
    return a + b;
}
sum(10);
sum(10, 20);
```

## 5. 1st 프로젝트 - To do Application
- `npm i` 명령어를 사용하여 `package.json` 참고하여 `install`
- `typing` : 타입이 정의되지 않은 코드에 타입을 정의해 주는 작업
  - 기존의 javascript에 typescript를 반영하기 위하여 많이 사용
- `index.ts` 파일 참고
- `node`를 활용하여 컴파일 및 실행
```javascript
$ node *.js
```

## 6. Interface
- 서로간의 규칙을 정의한 것.
  - 객체의 속성, 타입 정의
  - 함수의 파라메터
  - 함수의 스펙
  - 배열과 객체의 접근 방식 정의
  - 클래스
  
### 6.1 함수의 인자(Parameter) 정의

```javascript
interface User {
    age: number;
    name: string;
}

var Hong: User = {
    age: 40,
    name: '홍길동',
};

function getUser(user: User) {
    console.log(user);
};
```
### 6.2 함수의 구조(Structure) 정의
```javascript
// 함수의 구조 정의
interface SumFunction {
    (a: number, b: number): number
}
var sum: SumFunction;
sum = function(a: number, b: number): number {
    return a + b;
}
console.log(sum(1,2));
```
### 6.3 배열과 객체 접근
```javascript
interface StringArray {
    [index: number]: string;
}
var arr: StringArray = ['a', 'b', 'c'];
arr[0] = '10';
console.log(arr);
```
### 6.4 딕셔너리(Dictionay) 정의
```javascript
interface StringRegexDictionary {
    [key: string]: RegExp;
}
var obj: StringRegexDictionary = {
    // sth: /abc/
    cssFile: /\.css$/, //css 확장자를 가지는 모든 파일
    jsFile: /\.js$/, //js 확장자를 가지는 모든 파일
};
// obj['cssFile'] = 'a'; //인터페이스에 위배하였음으로 오류 발생
Object.keys(obj).forEach(function(value) {
    
});
```
### 6.5 확장(상속)
```javascript
interface Person {
    name: string;
    age: number;
}
interface Developer extends Person {
    language: string;
}
var Hong1: Developer = {
    name: '홍길동',
    age: 100,
    language: 'Vue'
}
console.log(Hong1);
```

## 7. 타입 별칭
- [좋은 소프트웨어는 확장이 용이해야 한다는 원칙](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)
- `type` 키워드를 사용하여 `별칭`으로 사용 가능하다. 단 `type`으로 선언하면 `확장(상속)`이 불가능
- `type`은 `확장성`이 용이하지 않음으로 반드시 인지하고 사용해야 함
```javascript
type MyString = string;
var str: MyString = 'hello';
```
- Interface Sample
  - <img src="../../assets/images/posts/typescript-1/7.1_interface.png" width="50%"/>
- Type Sample
  - <img src="../../assets/images/posts/typescript-1/7.2_type.png" width="50%"/>

## 8. 연산자를 이용한 타입 정의
### 8.1 `Union Type`
  - 변수 또는 함수 매개 변수에 둘 이상의 데이터 형식을 사용
  ```javascript
  function logMessage(value: string | number) {
      if(typeof value == 'string') {
          console.log(value.toString());
      }
     if(typeof value == 'number') {
          console.log(value.toLocaleString());
      }
  }
  logMessage('HELLO');
  logMessage(100);
  ```
  - 두개 이상의 공통된 속성만 접근가능하며, 나머지는 타입가드 처리 필요
  ```javascript
    interface Developer {
        name: string,
        skill: string,
    }
    interface Person {
        name: string,
        age: number,
    }
    function askSomeone(someone: Developer | Person) {
        someone.name = '공동적인 이름';
        someone.skill = ''; //오류 발생
    }
    askSomeone({name: '개발자', skill: 'c#'});//모두 정의할 필요 없음
  ```

### 8.2 `Intersection Type`

  - 여러타입을 합쳐서 사용하는 타입
  ```javascript
    interface Developer {
        name: string,
        skill: string,
    }
    interface Person {
        name: string,
        age: number,
    }
    function askSomeone2(someone: Developer & Person) {
        someone.name = '';
        someone.skill = '';
        someone.age = 100;
    }
    askSomeone2({name: '개발자', skill: 'c#', age: 100});//모두 정의해야 함
  ```

### 8.3 `Type Guard`

  - 타입의 유효성 검사
  - 특정 타입으로 타입의 범위를 좁혀(필터링)나가는 과장
  ```javascript
  function logMessage(value: string | number) {
      if(typeof value == 'string') {
          console.log(value.toString());
      }
     if(typeof value == 'number') {
          console.log(value.toLocaleString());
      }
     throw new TypeError('value는 숫자나 문자여야 합니다');
  }
  ```

## 9. Enum
### 9.1 Enum
- 특정 값들의 집합 자료형
- enum sample #1
```javascript
enum Shose {
    Nike,
    Adias,
}
var MyShose = Shose.Nike;
console.log(MyShose); // '0'으로 출력
```
- enum sample #2
```javascript
enum Shose1 {
    Nike = '나이키',
    Adidas = '아디다스',
}
var myShose = Shose1.Nike;
console.log(myShose); // '나아키'로 출력
```

### 9.2 Enum 사용

```javascript
enum Answer {
    Yes = 'Y',
    No = 'N',
}
function askQuestion(answer: Answer) {
    if(answer == Answer.Yes) {
        console.log(`answer : ${answer}`, 'YES');
    }
    if(answer == Answer.No) {
        console.log(`answer : ${answer}`, 'NO');
    }
}
// askQuestion('yes');
// askQuestion('예스');
askQuestion(Answer.Yes);
```

## 10. Class
- [MDN 자바스크립트 프로토타입과 상속](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [MDN Object 문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object)

### 10.1 Class 기본 문법 예제

```typescript
class Person {
    constructor(name, age) {
        console.log('생성 완료');
        this.name = name;
        this.age = age;
    }
}
var hong = new Person('홍', 100);
console.log(hong);
```
### 10.2 프로토타입
- 자기 자신의 인서턴스 또는 객체를 생성할때의 원형을 의미
- <img src="../../assets/images/posts/typescript-1/10.2 class_prototype_1.png" width="80%"/>
- <img src="../../assets/images/posts/typescript-1/10.2 class_prototype_2.png" width="60%"/>

### 10.3 Object MDN(Mozilla Developer Network)

- `Bult-in Javascript API` 또는 `Javascript Native API`

### 10.4 Prototyp vs Class vs typescript

```javascript
// 이전의 생성자 함수를 작성하는 코드 패턴
function Person(name, age) {
    this.name = name;
    this.age = age;
}
var captOld = new Person('홍길동', 100);

// ES6에서 클래스를 사용하는 코드 패턴
class Person {
    constructor(name, age) {
        console.log('생성 완료');
        this.name = name;
        this.age = age;
    }
}
var captNew = new Person('홍길동', 100);
```
```javascript
// 7_class.ts 즉, 타입스크립트로 작성할 경우 형식에 대한 명확한 구현이 필요 함
class Person {
    private name: string;
    public age: number;
    readonly log: string;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
}
var hong = new Person('홍길동', 100);
```


## 11. Generic
- [제네릭 교안 바로가기](https://joshua1988.github.io/ts/guide/generics.html)

### 11.1 Generic 이란?
- C#, Java 등의 언어에서 재사용성이 높은 컴포넌트를 만들때 자주 사용하는 특징으로 중복 코드 작성을 최소화하여 여러가지 타입을 수용할 수 있도록 컴포넌트를 생성하기 위해서 사용한다.

```javascript
// 기존의 함수 및 인자 사용
function logText(text) {
    console.log(text);
    return text;
}
logText(10);
logText('Hi');
logText(true);

// 제너릭 타입 사용
function logText<T>(text: T) {
    console.log(text);
    return text;
}
logText<string>('Hi');
```

### 11.2 Union Type으로 Generic Type 해결
- `Union Type`으로 입력파라메터는 해결되나 `string`, `number`의 명시적 타입 오류 발생
```javascript
function logText(text: string | number) {
    console.log(text);
    return text;
}
const a = logText('a');
a.split(''); // Error 발생
logText(10);
```

### 11.3 Generic Sample #1
```javascript
function logText<T>(text: T): T {
    console.log(text);
    return text;
}
const str = logText<string>('abc');
str.split('');
const login = logText<boolean>(true);
```
### 11.4 Generic Sample #2
```javascript
// 인자값 정의
const emails: { value: string, selected: boolean }[] = [
  { value: 'naver.com', selected: true },
  { value: 'gmail.com', selected: false },
  { value: 'hanmail.net', selected: false },
];

const numberOfProducts: { value: number, selected: boolean }[] = [
  { value: 1, selected: true },
  { value: 2, selected: false },
  { value: 3, selected: false },
];

function createDropdownItem(item: {value: string, selected: boolean}) {
  const option = document.createElement('option');
  option.value = item.value.toString();
  option.innerText = item.value.toString();
  option.selected = item.selected;
  return option;
}

// NOTE: 이메일 드롭 다운 아이템 추가
emails.forEach(function (email) {
  const item = createDropdownItem(email);
  const selectTag = document.querySelector('#email-dropdown');
  selectTag.appendChild(item);
});
```
```javascript
// interface 정의
interface Email {
  value: string;
  selected: boolean;
}
interface ProductNumber {
  value: number;
  selected: boolean;
}

const emails: Email[] = [
  { value: 'naver.com', selected: true },
  { value: 'gmail.com', selected: false },
  { value: 'hanmail.net', selected: false },
];
const numberOfProducts: ProductNumber[] = [
  { value: 1, selected: true },
  { value: 2, selected: false },
  { value: 3, selected: false },
];

function createDropdownItem(item: Email | ProductNumber) {
  const option = document.createElement('option');
  option.value = item.value.toString();
  option.innerText = item.value.toString();
  option.selected = item.selected;
  return option;
}
emails.forEach(function (email) {
  const item = createDropdownItem(email);
  const selectTag = document.querySelector('#email-dropdown');
  selectTag.appendChild(item);
});
numberOfProducts.forEach(function (product) {
  const item = createDropdownItem(product);
});
```
### 11.5 Generic of Interface Sample
```javascript
interface DropDown {
    value: string;
    selected: boolean;
}
const obj: DropDown = { value: 'abc', selected: false };

interface DropDown<T> {
    value: T;
    selected: boolean;
}
const obj: DropDown<string> = { value: 'abc', selected: false };
const obj2: DropDown<number> = { value: 100, selected: true };
```
### 11.6 타입 제한
```javascript
// 'text.length'에서 오류 발생 : 제너릭 타입의 명시적 타입을 알 수 없다.
function logTextLength<T>(text: T) {
    console.log(text.length);
    return text;
}
// []와 같이 배열을 사용하면 'length' 속성 사용 가능
function logTextLength<T>(text: T[]): T[] {
    console.log(text.length);
    return text;
}
```
### 11.7 정의된 타입으로 타입 제한
```javascript
interface LengthType {
    length: number;
}
function logTextLength<T extends LengthType>(text: T) : T {
    text.length;
    return text;
}
logTextLength(10); // 오류 발생
logTextLength({ length: 10 });
logTextLength({ lengh: 5 }); // 오류 발생
```
### 11.8 `keyof`을 사용하여 제너릭 타입 제한
```javascript
interface ShoppingItem {
    name: string;
    price: number;
    stock: number;
}
function getShoppingItemOption<T extends keyof ShoppingItem>(itemOption: T): T {
    return itemOption;
}
getShoppingItemOption(10); // Error 발생
getShoppingItemOption<string>('a'); // Error 발생
getShoppingItemOption("price");
```

## 12. 2nd 프로젝트 - Phonebook Application
- `address-book` 프로젝트의 `src/index.ts` 파일을 `ES6` 문법을 적용하여 리팩토링
- `.eslintrc.js` 파일 수정
```javascript
// '@typescript-eslint/no-explicit-any': 'off',
// "@typescript-eslint/explicit-function-return-type": 'off',
```
- `tsconfig.json` 파일 수정
```javascript
"noImplicitAny": true,
"strict": true,
"strictFunctionTypes": true,
```

### 12.1 동기 방식 vs 비동기 방식
- 동기 방식
```javascript
function fetchItems(): string[] {
  let items = ['a', 'b', 'c'];
  return items;
}
let result = fetchItems();
console.log(result);

```
- 비동기 방식
```javascript
 function fetchItems1(): Promise<string[]> {
  let items: string[] = ['a', 'b', 'c'];
  return new Promise(function (resolve) {
    resolve(items);
  });
}
fetchItems1();
```

## 13. 타입 추론
- 타입 추론
  - 타입스크립트가 코드를 해석해 나가는 방식
- [타입 추론](https://joshua1988.github.io/ts/guide/type-inference.html#%ED%83%80%EC%9E%85-%EC%B6%94%EB%A1%A0-type-inference)
- `ES6`에서 타입 추론은 기본 파라메터, 리턴타입등을 자동으로 판단

### 13.1 일반적인 타입 추론

```javascript
var a = '10';

function getB(b = 10) {
    var c = 'hi';
    return c+b;
}
```
### 13.2 인터페이스와 제너릭을 이용한 타입 추론
```javascript
interface Dropdown<T> {
    value: T;
    title: string;
}
var shoppingItem: Dropdown<string> = {
    value: 'abc',
    title: 'hello',
}
```
### 13.3 복잡한 구조에서의 타입 추론
```javascript
interface Dropdown<T> {
    value: T;
    title: string;
}

var shoppingItem: Dropdown<string> = {
    value: 'abc',
    title: 'hello',
}

var detailedItem: DetailedDropdown<number> = {
    title: 'title',
    description: 'description',
    value: 10,
    tag: 20,
}
```
### 13.4 Best Common Type 추론 방식
- 몇 개의 표현식(코드)을 바탕으로 타입을 추론한다. 가장 근접한 타입을 추론한다.
```javascript
var arr = [1, 2, true, true, 'a'];
```

### 13.5 Typescript Language Server
- [VSCode 타입스크립트 소개 문서](https://code.visualstudio.com/docs/languages/typescript#_code-suggestions)
- [VSCode Language Server Extension 가이드](https://code.visualstudio.com/api/language-extensions/language-server-extension-guide)
- [Language Server 소개 사이트](https://langserver.org/)
- [Language Server Protocol 개요](https://docs.microsoft.com/ko-kr/visualstudio/extensibility/language-server-protocol?view=vs-2019)

## 14. 타입 단언
### 14.1 타입 단언(Type Assertion)
- 컴파일러에게 타입에 대해서 더 명확하게 인지하고 있다는 키워드 `as`

```javascript
var a;
a = 'hi';
a = 20;
var b = a as number;

let div = document.querySelector('div') as HTMLDivElement;
if (div) {
    div.innerText;
}
```

## 15. 타입 가드
### 15.1 타입 가드
- 타입 단언(Type Assertion)으로 구현된 경우 타입 가드를 구현하는 패턴

```javascript
// 타입 단언 패턴을 사용하여 구현
interface Developer {
    name: string;
    skill: string;
}
interface Person {
    name: string;
    age: number;
}

function introduce(): Developer | Person {
    return { name: 'Tony', age: 33, skill: 'c#' }
}

var tony = introduce();
console.log(tony);

if((tony as Developer).skill) {
    var skill = (tony as Developer).skill;
    console.log(skill);
} else if((tony as Person).age) {
    var age = (tony as Person).age;
    console.log(age);
}

// 타입 가드 패턴을 사용하여 구현
function isDeveloper(target: Developer | Person): target is Developer {
    return (target as Developer).skill != undefined;
}
if(isDeveloper(tony)) {
    console.log(tony.skill);
} else {
    console.log(tony.age);
}
```

## 16. 타입 호환
### 16.1 타입 호환
- [타입 호환이란] (https://joshua1988.github.io/ts/guide/type-compatibility.html)
- 타입 스크립트에서 속성이 더 많은 타입이 더 작은 타입을 포함하여 호환 된다

### 16.2 Interface, Class
```javascript
interface Developrt {
    name: string;
    skill: string;
}
interface Person {
    name: string;
}
var developer: Developrt;
var person: Person;
developer = person; // Error 발생
person = developer;
```
```javascript
interface Developrt {
    name: string;
    skill: string;
}
class Person {
    name: string;
    skill: string;
}
var developer: Developrt;
var person: Person;
developer = person;
person = developer;
developer = new Person();
```
### 16.3 Function, Generic
```javascript
// 함수
var add = function(a: number) {
    // ...
}
var sum = function(a: number, b: number) {
    // ...
}
sum = add;
add = sum; // Error 발생

// 제너릭
interface Empty<T> {
    // ...
}
var empty1: Empty<string>;
var empty2: Empty<number>;
empty1 = empty2;
empty2 = empty1;

interface NotEmpty<T> {
    data: T;
}
var notempty1: NotEmpty<string>;
var notempty2: NotEmpty<number>;
notempty1 = notempty2; // string, number 타입 오류 발생
notempty2 = notempty1; // number, string 타입 오류 발생
```

## 17. 타입 모듈화
### 17.1 타입 모듈화
- [타입스크립트의 모듈화](https://joshua1988.github.io/ts/usage/modules.html)
- [ES6+ > Modules](https://babeljs.io/docs/en/learn#modules) 개념과 유사
- `export`, `import` 키워드를 사용하여 타입 정의에 대해서 모듈화

```javascript
// types.ts
interface Todo {
    title: string;
    checked: boolean;
}

export {
    Todo
};
// app.ts
import { Todo } from './types';

var item: Todo = {
    title: '할일',
    checked: false,
}
```
- [ES6 Modules](https://joshua1988.github.io/vue-camp/es6+/modules.html)
- [자바스크립트 모듈화 역사](https://d2.naver.com/helloworld/12864)
  
## 18. 출처
- [인프런](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%85%EB%AC%B8/dashboard)
