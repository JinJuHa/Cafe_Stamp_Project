# vue-project

## MY-STAMP
My Stamp는 카페 도장 쿠폰 솔루션을 제공해주는 웹사이트 입니다.
<img src="public/logo.png" style="width: 450px" />

## 디렉토리 및 파일 구조
```
├── .vscode                         # VSCode 관련 환경 세팅 디렉토리
│   └── settings.json
├── node_modules                    # 'npm install'을 통해 설치되는 모듈 파일 디렉토리
│   └── ...
├── public                          # index.html 과 각종 이미지 파일이 들어있는 공간
│   └── ...
├── src                             # 각종 vue파일과 js파일들이 작성되는 공간
│   ├── assets                      # 정적파일 서비스 공간
│   │   └── img                    # 파일 내에서 사용되는 이미지 파일들
│   │   └── mixins                # 전역으로 사용되는 vue 파일들
│   │   └── style                   # css파일들
│   ├── components                  # 각종 component 공간
│   │   ├── cafe                     # 카페 컴포넌트
│   │   │   └── cafeList.vue         # 카페 리스트 컴포넌트
│   │   ├── qna                     # qna 컴포넌트
│   │   │   └── qnaList.vue         # qna 리스트 컴포넌트
│   │   ├── layout                  # 레이아웃 컴포넌트(헤더, 사이드바)
│   │   │   └── Header.vue         # 헤더 컴포넌트
│   │   └── NotFound.vue            # File Not Found 컴포넌트(404 처리 컴포넌트)
│   ├── router                      # 라우터 관련 디텍토리
│   │   └── index.js                # 라우터 파일
│   ├── views                       # 페이지 뷰(화면)파일 디렉토리
│   │   ├── auth                    # 로그인 화면 처리 디렉토리
│   │   ├── device                 # PC가 아닌 다른 기기(모바일, 템플릿) 화면 처리 디렉토리
│   │   ├── main                   # 메인 화면 처리 디렉토리
│   │   ├── convention.vue         # 솔루션 제공 및 광고 화면 처리 파일 | 협약 기업
│   │   ├── FQ.vue                     # 솔루션 제공 및 광고 화면 처리 파일 | 자주 묻는 질문과 답변 FAQ
│   │   ├── introduce.vue            # 솔루션 제공 및 광고 화면 처리 파일 | 자주 묻는 질문과 답변 FAQ
│   │   ├── Home.vue                # 솔루션 제공 및 광고 화면 처리 파일 | 개발 크루 소개
│   │   └── index.vue                # Body부분의 화면 파일 | Home 화면을 제어하는 파일
│   ├── App.vue                     # 전체 화면 제어 파일
│   └── main.js                     # vuejs의 메인 실행 파일
├── .env                            # 환경설정 파일
├── .eslintrc.js                    # eslint 환경설정 파일
├── .gitignore                      # git의 ignore설정 파일
├── babel.config.js
├── dockerBuild.sh                  # docker build를 실행시키기 위한 파일
├── Dockerfile                      # docker 이미지를 만들기 위한 파일
├── dockerRun.sh                    # docker 컨테이너를 만들기 위한 파일
├── nginx-default.conf              # docker내의 nginx 설정 파일
├── package-lock.json
├── package.json                    # nodejs 패키지 파일(npm install관련)
├── README.md
└── vue.config.js                   # vue설정 파일(proxy 설정)
```

## 백엔드 연동
본 프로젝트와 연동되는 백엔드는 `cafe-backend`를 사용합니다.
(https://github.com/RedPanda6801/cafe-backend)


## 개발 환경
개발용 PC의 OS는 `windows 10`을 사용 합니다.


## vue-cli 설치 옵션
```console
Vue CLI v4.5.15
? Please pick a preset: Manually select features
? Check the features needed for your project: Choose Vue version, Babel, Router, Vuex, Linter
? Choose a version of Vue.js that you want to start the project with 2.x
? Use history mode for router? (Requires proper server setup for index fallback in production) Yes
? Pick a linter / formatter config: Prettier
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
? Save this as a preset for future projects? (y/N) N
```

## eslint + prettier 설정
> /.eslintrc.js
```javascript
module.exports = {
  root: true,
  env: {
    node: true,
  },
  // extends: ["plugin:vue/essential", "eslint:recommended", "@vue/prettier"],
  extends: ["plugin:vue/recommended", "eslint:recommended", "@vue/prettier"],
  parserOptions: {
    parser: "babel-eslint",
  },
  rules: {
    "prettier/prettier": [
      "error", {
        singleQuote: true,
        semi: false,
        useTabs: false,
        tabWidth: 2,
        trailingComma: "none",
        printWidth: 120,
        bracketSpacing: true,
        arrowParens: "avoid",
        endOfLine: "auto",
      }
    ],
    "no-console": process.env.NODE_ENV === "production" ? "warn" : "off",
    "no-debugger": process.env.NODE_ENV === "production" ? "warn" : "off",
    "no-unused-vars": ["warn", { vars: "all", args: "after-used", ignoreRestSiblings: false }],
  },
};
```

## VS Code의 setting.json 설정
`VS Code`의 `File > Preferences > Setting -> Workspace -> Text Editor > Code Actions On Save --> Edit in settings.json`

> /.vscode/settings.json
```json
{
  "eslint.validate": [
    "vue", "javascript", "html"
  ],
  "eslint.alwaysShowStatus": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
}
```

## bootstrap-vue 설치
```console
> npm install bootstrap@4.5.3 bootstrap-vue@2.21.2 --save
```
> /src/main.js
```javascript
import Vue from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'

// bootstrap
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)
Vue.use(IconsPlugin)

Vue.config.productionTip = false

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount('#app')
```

## main.css 스타일 시트

### 스타일 시트

> /src/assets/style/main.css

## 페이지 분할

##### 다음과 같이 `Header`, `Content`로 나뉜다. 

다음의 위치에 각각의 파일이 생성되어 있다.

Header 파일: `/src/components/layout/Header.vue`
Content 파일: `/src/views/Home.vue`

##### `NotFound`처리 파일도 생성 되어 있다.

NotFound 파일: `/src/components/NotFound.vue`

### Router 설정

1) `/`로 방문 시 `/home`으로 리다이렉트 시킨다.  
2) `/`의 하위구조를 모두 `children`으로 잡는다.  
3) `*`의 설정을 통해 `File not found`를 처리하도록 한다.  

> /src/router/index.js

```javascript
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)

const routes = [
  {
    path: '/',
    component: () => import('../views'),
    redirect: '/home',
    children: [
      {
        path: '/home',
        component: () => import('../views/Home.vue')
      }
    ]
  },
  {
    path: '*',
    component: () => import('../components/NotFound.vue')
  }
]

const router = new VueRouter({
  mode: 'history',
  base: process.env.BASE_URL,
  routes
})

export default router
```


### .env 파일
> /.env
```
NODE_ENV=production
VUE_APP_SERVER=http://localhost:3000
```
`vue`에서 `.env`파일의 환경설정을 읽기 위해서는 반드시 `VUE_APP_`라는 접두사를 사용해야 한다.
이는 `process.env.VUE_APP_`를 통해 추출할 수 있다.

**주의** `VUE_APP_SERVER`에는 백엔드 서버의 값을 설정해야 한다.


## CRUD 기능

### 리스트 화면 제작

우선 부서관리 리스트 화면을 제작 해보자.

##### 1) 리스트 화면 작성

다음과 같이 부서관리 페이지에 테이블(`<b-table>`)을 만든다. 
`fields`는 실제 연동할 필드로 작성 한다.
`items`는 테스트용 데이터를 작성 한다. (추후 삭제 예정)

> /src/views/department/index.vue
```html
<template>
  <div>
    <h1>부서 관리</h1>
    <div style="margin-bottom: 5px">
      <b-row>
        <b-col style="text-align: left"><b-button variant="primary" size="sm">검색</b-button></b-col>
        <b-col style="text-align: right"><b-button variant="success" size="sm">신규등록</b-button></b-col>
      </b-row>
    </div>
    <div>
      <b-table small hover striped :items="items" :fields="fields">
        <template #cell(createdAt)="row">
          {{ row.item.createdAt.substring(0, 10) }}
        </template>
      </b-table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fields: [
        { key: 'id', label: 'id' },
        { key: 'name', label: '부서명' },
        { key: 'code', label: '부서코드' },
        { key: 'createdAt', label: '생성일' }
      ],
      items: [
        { id: 1, name: '개발팀', code: 'dev', createdAt: '2021-12-01T00:00:00.000Z' },
        { id: 2, name: '영업팀', code: 'sales', createdAt: '2021-12-01T00:00:00.000Z' }
      ]
    }
  }
}
</script>
```

### 에러 메세지의 구조화
프론트 화면에서의 에러 메세지 구조화 예시
```json
"Error": {
  "400": "입력 정보를 확인해 주세요",
  "401": "로그인 시간이 만료되었습니다.",
  "403": "실행 권한이 없습니다.",
  "404": "API Call Error",
  "500": "Internal Server Error",
  "requestFail": "서버와의 연결이 끊어졌습니다."
},
```

<!-- ### console.log의 제거
`console.log`는 운영 상태의 시스템에서는 사용되어서는 안된다.
개발이 끝난 컴포넌트는  반드시 `console.log`는 주석처리 or 삭제처리 하도록 한다. 

console정보를 삭제해야 하는 이유
- 보안상 노출하지 말아야 할 정보가 노출되는 경우가 생긴다
- 너무 많은 console정보로 인해 디버깅이 힘들어 진다.
- console에 많은 데이터를 쌓게되면 클라이언트 PC에 부담이 생긴다.(사이트가 느려지는 효과 발생) -->


## 로그인
로그인/아웃 처리는 `jwt`를 발행/폐기 하는 방식으로 처리 한다.
발급된 토큰정보는 웹브라우저의 `localStorage`에 저장한다. 
응답 받을때 토큰은 `response.headers.token`에 전송 받는다. (백엔드의 API를 확인할 것)

### 로그인 화면
로그인 화면은 상단의 `app-header`부분 없이 독립된 디자인의 페이지로 생성했다.

