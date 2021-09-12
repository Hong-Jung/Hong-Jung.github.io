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
last_modified_at: 2021-09-11
---

## 1. What is 'Vue'

### 1.1 Vue ??
  
  * 내용 입력<br/>
  <img src="../../assets/images/posts/vue-intermediate/vue-2-1.png" width="60%" height="30%" title="Vue 구조" alt="툴팁"/>

```html
<!--watch 샘플-->
<div id="app">
    {{ num }}
    <button v-on:click="addNum">increase</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    new Vue({
        el: '#app',
        data: {
            num: 10
        },
        watch: {
            num: function(val, oldVal) {
                this.logText(val, oldVal);
            }
        },
        methods: {
            addNum: function() {
                this.num = this.num + 1;
            },
            logText: function(val, oldVal) {
                console.log('new: %s, old: %s', val, oldVal);
            }
        }
    });
</script>
```

## 4. 참고 사항

### 4.1 Troubleshooting

  * GitHub 싱크후 ‘npm run serve’시 명령어 인식 불가할 경우 하기와 같이 명령서 실행
  
```
npm i @vue/cli-service
```

### 4.2 출처

  * [인프런](https://www.inflearn.com/course/Age-of-Vuejs)
