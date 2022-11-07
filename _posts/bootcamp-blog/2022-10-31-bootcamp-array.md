---
title:  "[Blog] JavaScript in Arrary."
excerpt: "개발자의품격"
comments: true
header:
  t

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격, Arrary]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-11-06
last_modified_at: 2022-11-06
---

# What is ***Arrary(배열)*** in JavaScript ?

## 0. Index

- [What is ***Arrary(배열)*** in JavaScript ?](#what-is-arrary배열-in-javascript-)
  - [0. Index](#0-index)
  - [1. Introduction](#1-introduction)
    - [1.1 배열(Arrary) 객체란 ?](#11-배열arrary-객체란-)
    - [1.2 배열은 왜 필요할까 ?](#12-배열은-왜-필요할까-)
    - [1.3 배열 객체의 내장 함수 종류는 ?](#13-배열-객체의-내장-함수-종류는-)
  - [2. Body](#2-body)
    - [2.1 toString()](#21-tostring)
    - [2.2 join()](#22-join)
    - [2.3 push()](#23-push)
    - [2.4 unshift()](#24-unshift)
    - [2.5 pop()](#25-pop)
    - [2.6 shift()](#26-shift)
    - [2.7 splice()](#27-splice)
    - [2.8 concat()](#28-concat)
    - [2.9 slice()](#29-slice)
    - [2.10 sort()](#210-sort)
    - [2.11 filter()](#211-filter)
    - [2.12 map()](#212-map)
    - [2.13 reduce()](#213-reduce)
  - [3. Conclusion](#3-conclusion)
  - [4. Reference](#4-reference)

## 1. Introduction 

- 블로그에서 다루는 내용
  - 자바스크립트에서는 기본 데이터 타입이 몇가지 있습니다. 그중 반드시 알아야하며, 가장 많이 사용하는 기본 데이터 타입 객체가 다음과 같습ㄴ다.
    - 문자열, 숫자형, 참/거짓, undefined, null, object, arrary
  - 몇가지 기본 데이터 타입중에서 이번 블로그에서는 array object에 대해서 중점적으로 알아 보겠습니다.
  - Arrary Object가 무엇인지, 왜 필요해서 우리가 알아야 하는지, 상세한 내장 함수(객체 하위의 function 또는 property)는 어떠한 것들이 존재하는지 마지막으로 그래서 어디서 활용하는지 알아보겠습니다.

### 1.1 배열(Arrary) 객체란 ?

- [MDN Site에서의 Array 객체의 설정/정의](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)
  - `리스트 형태의 고수준 객체인 배열을 생성할 때 사용하는 전역 객체`
    - 리스트형태 즉, 목록의 형태를 띠는 객체이다. 즉, 무엇인지 모르지만 개발자가 작성하게 될 값이 목록의 형태를 가지고 있습니다.
  - `배열의 요소 인덱스로 문자열을 사용할 수 없으며 무조건 정수만 허용` 
    - 배열의 목록에 접근하기 위해서는 정수(인덱스, 번호)로만 지정하여 사용가능 합니다.

```javascript
// 0.1 배열 만들기
let fruits = ['사과', '바나나']

console.log(fruits.length)
// 2

// 0.2 인덱스로 배열의 항목에 접근하기
let first = fruits[0]
// 사과

let last = fruits[fruits.length - 1]
// 바나나

// 0.3 배열의 항목들을 반복하며 처리하기
fruits.forEach(function (item, index, array) {
  console.log(item, index)
})
// 사과 0
// 바나나 1
```

### 1.2 배열은 왜 필요할까 ?

- 배열(Array)은 *서로 관련이 있는 데이터끼리의 모음*으로 하나의 모음으로 관리하기 위한 데이터 타입의 한 종류 이며, 객체 입니다.
  - 실제 코딩의 경우를 생각해 봅시다. (Case Study)
    - 시험 점수 5개가 존재 한다고 가정하며, 각 데이터는 다음과 같습니다.
    - score1 ~ score5
    - 배열 없이 일반 변수로 5개의 데이터를 정의하고 할당하며, 출력 합니다.

    - ```javascript
      let score1 = 65;
      let score2 = 70;
      let score3 = 89;
      let score4 = 94;
      let score5 = 85;

      console.log(score1);//output: 65
      console.log(score2);//output: 70
      console.log(score3);//output: 89
      console.log(score4);//output: 94
      console.log(score5);//output: 85
      ```

    - 쉽죠? 5개 변수를 선언하고 각 선언한 변수에 데이터베이스로부터 수신한 값? 또는 로직으로 사용할 값을 할당 합니다. 각 할당한 값을 하나씩 출력해 봅니다.
    - 자, 여기서 다음의 요구사항? 요건에 대해서 어떤 해결책이 있을까요?
      - 5개의 변수의 값을 하나의 문자열로 합치고 싶다면?
      - 점수가 추가되어 더하고 싶다면?
      - 점수 기준으로 오름차순 혹은 내림차순으로 정렬하고 싶다면?
    - 해결책은 너무도 다양 합니다. 이러한 요구사항의 해결책을 어떠한 것이 최선일까?라는 문제로 접근할 것이 아니라, 이미 **이러한 요구사항의 해결책을 위하여 만들어 놓은 것이 Array 객체가 그중 하나** 입니다.
  
    - ```javascript
      let score = [65, 70, 89, 94, 85];
      console.log(score);
      //output: Array(5) [ 65, 70, 89, 94, 85 ]
      ```

    - 3가지 요구사항뿐 아니라, 더 많은 요구의 해결을 위한 Array 객체의 하위에 함수나 속성 형태로 이미 제공되고 있습니다. 우리는 이미 만들어진 함수나 속성에 대해서 정확한 쓰임새를 익힘으로 무한의 활용이 가능해 집니다.
      - 1차원 배열의 경우는 위의 샘플 코드와 같이 하나의 연관 데이터(John Doe)만 정의하지만, 2차원 배열의 경우 연관된 데이터의 묶음을 무수하게 정의하고, 정의된 배열 객체의 데이터를 손쉽게 다룰 수 있습니다.

### 1.3 배열 객체의 내장 함수 종류는 ?

|                                                 함수 이름                                                  | 간략 설명                                                             |
| :--------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------- |
| [toString()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) | 문자열 객체로 변환하여 반환                                           |
|     [join()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)     | 파라미터의 문자가 요소 사이 삽입되어 하나의 문자로 반환               |
|     [push()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push)     | 파라미터의 문자를 마지막 요소로 추가                                  |
|  [unshift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)  | 파라미터의 문자를 첫번째 요소로 추가                                  |
|      [pop()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)      | 마지막 요소 제거 후 반환                                              |
|    [shift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)    | 첫번째 요소 제거 후 반환                                              |
|   [splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)   | 특정 위치에 요소 추가, 추가시 삭제도 가능                             |
|   [concat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)   | 2개 이상의 배열 결합                                                  |
|    [slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)    | 요소를 잘라내서 배열 타입으로 반환                                    |
|     [sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)     | 요소를 정렬                                                           |
|   [filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)   | 특정 조건의 요소를 찾고 배열로 반환                                   |
|      [map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)      | 배열의 요소가 객체의 경우(key-value), 새로운 객체로 변경 후 배열 반환 |
|   [reduce()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)   | 요소의 크기만큼 callback 호출(재귀 호출)하면서 누적된 값을 출력       |

## 2. Body

### 2.1 toString()

- [toString()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)
  
> 문자열 객체로 변환하여 반환
>>
>> ```javascript
>> let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
>> console.log(brands.toString());
>> // Output:
>> // 애플,구글,아마존,마이크로소프트,메타
>> ```

### 2.2 join()

- [join()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)
  
> 파라미터의 문자가 요소 사이 삽입되어 하나의 문자로 반환
>>
>> ```javascript
>> console.log(brands.join(" * "));
>> // Output:
>> // 애플 * 구글 * 아마존 * 마이크로소프트 * 메타
>> console.log(brands.join(""));
>> // Output:
>> // 애플구글아마존마이크로소프트메타
>> ```

### 2.3 push()

- [push()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
  
> 파라미터의 문자를 마지막 요소로 추가
>>
>> ```html
>> <button onclick="doSearch();">조회</button>
>> <table>
>> <thead>
>>     <th>음료</th>
>>     <th>가격</th>
>>   </thead>
>>   <tbody id="tbBody"></tbody>
>> </table>
>> ```
>>
>> ```javascript
>> function doSearch() {
>>   const drinkList = [
>>     {
>>       name: "오렌지",
>>       price: 1000,
>>     },
>>     {
>>       name: "파워레이드",
>>       price: 1400,
>>     },
>>     {
>>       name: "커피",
>>       price: 700,
>>     },
>>     {
>>       name: "보리음료",
>>       price: 1200,
>>     },
>>     {
>>       name: "코카콜라",
>>       price: 1000,
>>     },
>>   ];
>> 
>>   // push()
>>   let trTags = [];
>>   for (const drink of drinkList) {
>>     trTags.push("<tr>");
>>     trTags.push("<td>" + drink.name + "</td>");
>>     trTags.push("<td>" + drink.price + "</td>");
>>     trTags.push("</tr>");
>>   }
>> 
>>   console.log(trTags.join(""));
>>   document.getElementById("tbBody").innerHTML = trTags;
>> }
>> ```

### 2.4 unshift()

- [unshift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
  
> 파라미터의 문자를 첫번째 요소로 추가, push가 일반적이나 태그 밖으로 뺄때는 unshift가 더 효율적임
>> 
>> ```javascript
>> let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
>> brands.unshift("삼성전자");
>> // Output:
>> // 6
>> console.log(brands);
>> // Output:
>> // Array(6) [ "삼성전자", "애플", "구글", "아마존", "마이크로소프트", "메타" ]
>> ```
>>
>> ```javascript
>> function loadDrinkType() {
>>   const types = [
>>     { text: "이온음료", code: "A" },
>>     { text: "커피", code: "B" },
>>     { text: "탄산음료", code: "C" },
>>   ];
>>   const h = [];
>>   for (const type of types) {
>>     h.push(
>>       '<option value="' + type.code + '">' + type.text + "</option>"
>>     );
>>   }
>>   return h;
>> }
>> const selDrinkType = loadDrinkType();
>> selDrinkType.unshift('<option value=""></option>');
>> document.getElementById("selDrinkType").innerHTML = selDrinkType.join("");
>> ```

### 2.5 pop()

- [pop()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
  
> 마지막 요소 제거 후 반환
>>
>> ```javascript
>> let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
>> console.log(brands.pop());
>> // Output: 
>> // 메타
>> console.log(brands);
>> // Output: 
>> // Array(4) [ "애플", "구글", "아마존", "마이크로소프트" ]
>> ```

### 2.6 shift()

- [shift()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)
  
> 첫번째 요소 제거 후 반환, shift는 메시지큐 처리에 많이 사용
>>
>> ```javascript
>> const array1 = [1, 2, 3];
>> const firstElement = array1.shift();
>> console.log(array1);
>> // Output: 
>> // Array [2, 3]
>> console.log(firstElement);
>> // output:
>> // 1

### 2.7 splice()

- [splice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
  
> 특정 위치에 요소 추가, 추가시 삭제도 가능
>>
>> - 첫번째 파라미터 - 새로운 요소를 추가할 인덱스 번호
>> - 두번째 파라미터 - 요소를 추가하기전에 삭제할 요소 수
>> - 나머지 파라미터 - 추가할 요소
>>
>> ```javascript
>> let brands = ["애플", "구글", "아마존", "마이크로소프트", "메타"];
>> brands.splice(1, 0, "개발자의품격", "더그레잇");
>> console.log(brands);
>> // Output:
>> // Array(7) [ "애플", "개발자의품격", "더그레잇", "구글", "아마존", "마이크로소프트", "메타" ]
>> ```

### 2.8 concat()

- [concat()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
  
> 2개 이상의 배열 결합
>>
>> ```javascript
>> let arr1 = ["A", "B"];
>> let arr2 = ["C", "D"];
>> let arr3 = ["E", "F", "G"];
>> let arr4 = arr1.concat(arr2, arr3);
>> console.log(arr4);
>> // Output:
>> // Array(7) [ "A", "B", "C", "D", "E", "F", "G" ]
>> ```

### 2.9 slice()

- [slice()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
  
> 요소를 잘라내서 배열 타입으로 반환
>>
>> ```javascript
>> console.log(arr4.slice(1, 2));
>> // Output:
>> // Array [ "B" ]
>> ```

### 2.10 sort()

- [sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
  
> 요소를 정렬
>>
>> - 숫자정열시 함수에서 양수는 바꿈, 음수는 바꾸지 않은, 0 같음
>> - 배열내 객체의 정렬 샘플(숫자, 문자의 경우 차이점 이해해야함)
>>
>> ```javascript
>> let points = [40, 100, 1, 5, 25, 10];
>> console.log(points.sort());
>> // Output:
>> // Array(6) [ 1, 10, 100, 25, 40, 5 ]
>> const ascPoints = points.sort(function (a, b) {
>>   // a - 40, b-100
>>   // [40, 100, 1, 5, 25, 10]
>>   // a - 100, b - 1
>>   // [40, 1, 100, 5, 25, 10]
>>   // a - 100, b -5
>>   // [40, 1, 5, 100, 25, 10]
>>   // a - 100, b - 25
>>   // [40, 1, 5, 25, 100, 10]
>>   // [1, 5, 10, 25, 40, 100]
>>   // if (a > b) return 1;
>>   // else if (a < b) return -1;
>>   // else 0;
>>   return a - b;
>> });
>> console.log(ascPoints);
>> const descPoints = points.sort(function (a, b) {
>>   return b - a;
>> });
>> console.log(descPoints);
>> let drinkList = [
>>   {
>>     name: "오렌지",
>>     price: 1000,
>>   },
>>   {
>>     name: "파워레이드",
>>     price: 1400,
>>   },
>>   {
>>     name: "커피",
>>     price: 700,
>>   },
>>   {
>>     name: "보리음료",
>>     price: 1200,
>>   },
>>   {
>>     name: "코카콜라",
>>     price: 1000,
>>   },
>> ];
>> const userSortKey = "name";
>> const ascDrinkList = drinkList.sort(function (a, b) {
>>   if (a[userSortKey] > b[userSortKey]) return 1;
>>   else if (a[userSortKey] < b[userSortKey]) return -1;
>>   else 0;
>> });
>> console.log(ascDrinkList);
>> ```

### 2.11 filter()

- [filter()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
  
> 특정 조건의 요소를 찾고 배열로 반환
>>
>> ```javascript
>> let drinkList = [
>>   {
>>     name: "오렌지",
>>     price: 1000,
>>   },
>>   {
>>     name: "파워레이드",
>>     price: 1400,
>>   },
>>   {
>>     name: "커피",
>>     price: 700,
>>   },
>>   {
>>     name: "보리음료",
>>     price: 1200,
>>   },
>>   {
>>     name: "코카콜라",
>>     price: 1000,
>>   },
>> ];
>> let availableProduct = [];
>> const inputCoin = 1000;
>> availableProduct = drinkList.filter(function (drink) {
>>   return drink.price <= inputCoin;
>> });
>> console.log(availableProduct);
>> // Output:
>> // Array(3) [ {…}, {…}, {…} ]
>> //  0: Object { name: "오렌지", price: 1000 }
>> //  1: Object { name: "커피", price: 700 }
>> //  2: Object { name: "코카콜라", price: 1000 }
>> ```

### 2.12 map()

- [map()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
  
> 배열의 요소가 객체의 경우(key-value), 새로운 객체로 변경 후 배열 반환
>>
>> ```javascript
>> let userList = [
>>   {
>>     firstName: "재석",
>>     lastName: "유",
>>     email: "ryu@gmail.com",
>>   },
>>   {
>>     firstName: "종국",
>>     lastName: "김",
>>     email: "kim@gmail.com",
>>   },
>>   {
>>     firstName: "지효",
>>     lastName: "송",
>>     email: "song@gmail.com",
>>   },
>> ];
>> let newUserList = userList.map(function (user) {
>>   return {
>>     fullName: user.lastName + user.firstName,
>>     email: user.email,
>>   };
>> });
>> console.log(newUserList);
>> // Output:
>> // Array(3) [ {…}, {…}, {…} ]
>> //  0: Object { fullName: "유재석", email: "ryu@gmail.com" }
>> //  1: Object { fullName: "김종국", email: "kim@gmail.com" }
>> //  2: Object { fullName: "송지효", email: "song@gmail.com" }
>> ```

### 2.13 reduce()

- [reduce()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
  
>> 요소의 크기만큼 callback 호출(재귀 호출)하면서 누적된 값을 출력
>>
>> ```javascript
>> points = [40, 100, 1, 5, 25, 10];
>> let sum = points.reduce(function (accumulator, currentValue) {
>>   return accumulator + currentValue;
>> }, 0); 
>> 
>> console.log(sum);
>> drinkList = [
>>   {
>>     name: "오렌지",
>>     price: 1000,
>>   },
>>   {
>>     name: "파워레이드",
>>     price: 1400,
>>   },
>>   {
>>     name: "커피",
>>     price: 700,
>>   },
>>   {
>>     name: "보리음료",
>>     price: 1200,
>>   },
>>   {
>>     name: "코카콜라",
>>     price: 1000,
>>   },
>> ];
>> let drinkTotal = drinkList.reduce(function (total, drink) {
>>   return total + drink.price;
>> }, 0);
>> console.log(drinkTotal);
>> userList = [
>>   {
>>     firstName: "재석",
>>     lastName: "유",
>>     email: "ryu@gmail.com",
>>   },
>>   {
>>     firstName: "종국",
>>     lastName: "김",
>>     email: "kim@gmail.com",
>>   },
>>   {
>>     firstName: "지효",
>>     lastName: "송",
>>     email: "song@gmail.com",
>>   },
>>   {
>>     firstName: "가네",
>>     lastName: "김",
>>     email: "kim2@gmail.com",
>>   },
>> ];
>> let kims = userList.reduce(function (users, user) {
>>   if (user.lastName === "김") {
>>     users.push(user);
>>   }
>>   return users;
>> }, []);
>> console.log(kims);
>> ```

## 3. Conclusion

- JavaScript에서 Array 객체의 활용도나 사용빈도는 상당히 높은 편이다. 즉, 아주 자주 사용하게 된다는 의미이며, 자주 사용하는 만큼 반드시 알고 넘어가야할 객체 입니다.
- 배열에 값을 *넣기(push, unshift, splice)*, *빼기(pop, shift, slice)*, *찾기(filter)*, *결합하기(concat)*, *정렬하기(sort)*는 무엇보다 중요하며 자주 사용하게 될 것 입니다.
- `map()`의 경우 ES6에서 새롭게 추고된 내장 함수로 key-value의 형태를 뜀으로 Object와 아주 유사하지만 다음의 몇가지 큰 차이점이 있습니다.
  - Key로 모든 데이터 타입을 가짐
  - Key의 사이즈를 쉽게 알 수 있음(size property)
  - Index에 의한 순서를 보장
  
## 4. Reference

- [MDN Site - Arrary](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [W3 School](https://www.w3schools.com/html/html_images_imagemap.asp)