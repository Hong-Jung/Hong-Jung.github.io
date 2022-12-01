---
title:  "[Blog] Vuejs Router "
excerpt: "개발자의품격"
comments: true
header:
author_profile: false
sidebar_main: true

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, Vue, Router]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-12-02
last_modified_at: 2022-12-02
---

# **Router** & **3가지 방식** in Web Storage

## Introduction 

- 블로그에서 다루는 내용
  - contents
  - contents
  - contents

### Vuejs에서 라우터(Router)가 뭔가요?

- 정의
  - 사전적 의미
- 설명
- 설명

### 그럼 어디에서 사용하면 될까요?

- Storage가 왜 필요 할까 ?
  - 개발에서 아주 작은 어플리케이션도 데이터를 저장하고 저장된 데이터를 불러와 재사용하며 관리되는 형태가 대부분이다.
  - 이러한 데이터의 관리(추가, 사용, 변경, 삭제)를 위하여 일반적으로 데이터베이스(DataBase)를 사용한다.(최근은 데이터베이스(DataBase)를 위하여 클라우드(Cloud) 플랫폼을 많이 사용 중이다.)
  - 이렇게 데이터를 관리(추가, 사용, 변경, 삭제)하게 됨으로 어플케이션이 보다 거대해지고 복잡해 진다.
  - 이번 블로그는 데이터베이스(DataBase) 스토리지(Storage)는 제외하고, *웹 스토리(Web Storage)중 로컬(Local) & 세션(Session) 스토리지(Storage)에 대해서 알아본다*.
- 어디에서 사용될까 ?
  - 로컬 스토리지(Local Storage)와 세션 스토리지(Session Storage)는 ***저장의 범위, 기간***에서 큰 차이점이 있다고 할 수 있다. (둘다 데이터를 저장한다는 기능은 동일)
  - 클라이언트 리소스에 직접 접근하여 사용 될 수 있는 데이터의 경우 유용하다.
    - 웹 싸이트의 *테마, 언어 설정, 비밀번호 임시 저장* 등과 같이 *클라이언트에서만 저장*될 수 있는 모든 데이터는 가능 하다.
  
  > 퍼포먼스(Performance) 측면도 중요하지만, *<u>기능적인 측면으로 접근해 보자</u>*.<br>
  > *주요 문서의 내용을 기입하고 관리하는 웹 어플리케이션이 있다고 가정*하자.<br>
  >> 주요 문서의 내용을 완벽하게 작성했다면, 작성 후 저장이라는 기능을 통하여 데이터베이스로 작성된 문서의 내용을 저장한다. 저장된 데이터는 데이터베이스로부터 불러와 열람하거나 수정 또는 삭제가 가능하다.<br><br>
  >> 하지만, 데이터베이스에 저장하기전 즉, <u>작성이 완료되 경우가 아니라 본인만 열람하며 계속해서 수정해야 한다면 어떻게 될까? 그렇다, 기능적으로 해소할 수 있다</u>.<br><br>
  >> 이럴때, 로컬 스토리지(Local Storage) 또는 세션 스토리지(Session Storage)를 활용한다면, 데이터베이스에 저장하기 전 임시로 작성되는 내용에 대해서 충분히 관리(생성, 열람, 수정, 삭제) 가능하다.

## Index

- [**Router** \& **3가지 방식** in Web Storage](#router--3가지-방식-in-web-storage)
  - [Introduction](#introduction)
    - [Vuejs에서 라우터(Router)가 뭔가요?](#vuejs에서-라우터router가-뭔가요)
    - [그럼 어디에서 사용하면 될까요?](#그럼-어디에서-사용하면-될까요)
  - [Index](#index)
  - [Body](#body)
    - [Vuejs 기본 라우터 이해](#vuejs-기본-라우터-이해)
    - [첫번째, 기본 라우터 방식](#첫번째-기본-라우터-방식)
    - [두번재, 별도의 파일로 분리되는 방식](#두번재-별도의-파일로-분리되는-방식)
    - [세번재, 별도의 파일로 분리되면서 다운로드 특성이 반영된 방식](#세번재-별도의-파일로-분리되면서-다운로드-특성이-반영된-방식)
  - [Conclusion](#conclusion)
  - [Reference](#reference)
  
## Body

### Vuejs 기본 라우터 이해

- 내용
  
> **IMPORTANT**
> 
>> - 내용

```html
```

### 첫번째, 기본 라우터 방식

- 내용
  
> **IMPORTANT**
> 
>> - 내용

```html
```

### 두번재, 별도의 파일로 분리되는 방식

- 내용
  
> **IMPORTANT**
> 
>> - 내용

```html
```

### 세번재, 별도의 파일로 분리되면서 다운로드 특성이 반영된 방식

- 내용
  
> **IMPORTANT**
> 
>> - 내용

```html
```

## Conclusion

- 내용
  
## Reference

- [Official Router - v4.x](https://router.vuejs.kr/guide/index.html)