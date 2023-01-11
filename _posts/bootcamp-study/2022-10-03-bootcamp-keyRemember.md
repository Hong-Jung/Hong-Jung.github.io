---
title:  "Key Remember Things."
excerpt: "개발자의품격"
comments: true
header:

categories:
  - bootcamp
tags:
  - [Blog, bootcamp, 개발자의품격]

toc: true
toc_sticky: false
toc_label: "페이지 주요 목차" 
 
date: 2022-10-03
last_modified_at: 2022-10-03
---

- [Key Remember Things](#key-remember-things)
- [Vuejs](#vuejs)
- [Nodejs](#nodejs)
- [SQL](#sql)
- [10. 엑셀 업로드 및 파싱](#10-엑셀-업로드-및-파싱)

# Key Remember Things

- Research 관련 중요한 사항들을 정리하는 목적

# Vuejs

- Vuejs 관련

# Nodejs

- WebServer Configuration

# SQL

- SQL 관련된 주요 사항 기록

> **IMPORTANT**
>> 페이징 처리
>>
>> - SELECT * FROM table_name LIMIT 건수
>> - SELECT * FROM table_name WHERE 조건 LIMIT 시작인덱스, 가져올 건수
>> - SELECT * FROM table_name LIMIT 5 OFFSET 5; // postgresql 구문
>> - 한 페이지에 보여주는 행의 갯수 = 10 라면 ???
>>
>>> - (첫번째 페이지 번호 - 1) x 보여줄 행 갯수 = (1 - 1) x 10 = 0 = LIMIT 0, 10
>>> - (두번째 페이지 번호 - 1) x 보여줄 행 갯수 = (2 - 1) x 10 = 10 = LIMIT 10, 10
>>> - (세번째 페이지 번호 - 1) x 보여줄 행 갯수 = (3 - 1) x 10 = 30 = LIMIT 30, 10
>>> - (네번째 페이지 번호 - 1) x 보여줄 행 갯수 = (4 - 1) x 10 = 40 = LIMIT 40, 10

# 10. 엑셀 업로드 및 파싱

- 내용

> **IMPORTANT**
>> 타이틀
>>
>> - 컨텐츠

```html
```