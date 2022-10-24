# vue-project

## MY-STAMP
My Stamp는 카페 도장 쿠폰 솔루션을 제공해주는 웹사이트 입니다.
<img src="public/logo.png" />

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

### 스타일 시트 생성

> /src/assets/style/main.css

## 페이지 분할

##### 다음과 같이 `Header`, `Content`로 나뉜다. 

다음의 위치에 각각의 파일을 생성 한다. (파일 내용은 타이틀만 써주자)

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


##### 1) Store 작성
`UpdatedResult`밑에 `DeletedResult`를 만들어 준다.

> /src/store/models/department.js
```javascript
import api from '../apiUtil'

// 초기값 선언
const stateInit = {
  Department: {
    id: null,
    name: null,
    code: null,
    description: null,
    createdAt: null,
    updatedAt: null
  }
}

export default {
  state: {
    DepartmentList: [],
    Department: { ...stateInit.Department },
    InsertedResult: null, // 입력처리 후 결과
    UpdatedResult: null, // 수정처리 후 결과
    DeletedResult: null, // 삭제처리 후 결과
    InputMode: null // 입력모드(등록: insert, 수정: update)
  },
  getters: {
    DepartmentList: state => state.DepartmentList,
    Department: state => state.Department,
    DepartmentInsertedResult: state => state.InsertedResult,
    DepartmentUpdatedResult: state => state.UpdatedResult,
    DepartmentDeletedResult: state => state.DeletedResult,
    DepartmentInputMode: state => state.InputMode
  },
  mutations: {
    setDepartmentList(state, data) {
      state.DepartmentList = data
    },
    setDepartment(state, data) {
      state.Department = data
    },
    setInsertedResult(state, data) {
      state.InsertedResult = data
    },
    setUpdatedResult(state, data) {
      state.UpdatedResult = data
    },
    setDeletedResult(state, data) {
      state.DeletedResult = data
    },
    setInputMode(state, data) {
      state.InputMode = data
    }
  },
  actions: {
    // 부서 리스트 조회
    actDepartmentList(context, payload) {
      /* 테스트 데이터 세팅 */
      const departmentList = [
        { id: 1, name: '개발팀', code: 'dev', createdAt: '2021-12-01T00:00:00.000Z' },
        { id: 2, name: '영업팀', code: 'sales', createdAt: '2021-12-01T00:00:00.000Z' }
      ]
      context.commit('setDepartmentList', departmentList)

      /* RestAPI 호출 */
      /*
      api.get('/serverApi/departments').then(response => {
        const departmentList = response && response.data
        context.commit('setDepartmentList', departmentList)
      })
      */
    },
    // 부서 입력
    actDepartmentInsert(context, payload) {
      // 상태값 초기화
      context.commit('setInsertedResult', null)

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        const insertedResult = 1
        context.commit('setInsertedResult', insertedResult)
      }, 300) // state값의 변화를 감지하기 위하여 일부러 지연 시켰다.

      /* RestAPI 호출 */
      /*
      api.post('/serverApi/departments').then(response => {
        const insertedResult = response && response.insertedId
        context.commit('setInsertedResult', insertedResult)
      })
      */
    },
    // 부서정보 초기화
    actDepartmentInit(context, payload) {
      context.commit('setDepartment', { ...stateInit.Department })
    },
    // 입력모드 설정
    actDepartmentInputMode(context, payload) {
      context.commit('setInputMode', payload)
    },
    // 부서 상세정보 조회
    actDepartmentInfo(context, payload) {
      // 상태값 초기화
      context.commit('setDepartment', { ...stateInit.Department })

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        const departmentList = [
          { id: 1, name: '개발팀', code: 'dev', description: '개발팀 테스트', createdAt: '2021-12-01T00:00:00.000Z' },
          { id: 2, name: '영업팀', code: 'sales', description: '영업팀 테스트', createdAt: '2021-12-01T00:00:00.000Z' }
        ]

        let department = { ...stateInit.Department }
        for (let i = 0; i < departmentList.length; i += 1) {
          if (payload === departmentList[i].id) {
            department = { ...departmentList[i] }
          }
        }
        context.commit('setDepartment', department)
      }, 300)

      /* RestAPI 호출 */
      /*
      api.get('/serverApi/departments/${payload}').then(response => {
        const department = response && response.department
        context.commit('setDepartment', department)
      })
      */
    },
    // 부서 수정
    actDepartmentUpdate(context, payload) {
      // 상태값 초기화
      context.commit('setUpdatedResult', null)

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        const updatedResult = 1
        context.commit('setUpdatedResult', updatedResult)
      }, 300) // state값의 변화를 감지하기 위하여 일부러 지연 시켰다.

      /* RestAPI 호출 */
      /*
      api.put('/serverApi/departments/${payload}').then(response => {
        const updatedResult = response && response.updatedCount
        context.commit('setUpdatedResult', updatedResult)
      })
      */
    },
    // 부서 삭제
    actDepartmentDelete(context, payload) {
      // 상태값 초기화
      context.commit('setDeletedResult', null)

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        const deletedResult = 1
        context.commit('setDeletedResult', deletedResult)
      }, 300) // state값의 변화를 감지하기 위하여 일부러 지연 시켰다.

      /* RestAPI 호출 */
      /*
      api.delete('/serverApi/departments/${payload}').then(response => {
        const deletedResult = response && response.deletedCount
        context.commit('setDeletedResult', deletedResult)
      })
      */
    }
  }
}
```

##### 2) 리스트 페이지에 [삭제]버튼 만들기
> /src/views/department/index.vue
```html
<template>
  <div>
    <h1>부서 관리</h1>
    <div style="margin-bottom: 5px">
      <b-row>
        <b-col style="text-align: left">
          <b-button variant="primary" size="sm" @click="searchDepartmentList">검색</b-button>
        </b-col>
        <b-col style="text-align: right">
          <b-button variant="success" size="sm" @click="onClickAddNew">신규등록</b-button>
        </b-col>
      </b-row>
    </div>
    <div>
      <b-table small hover striped :items="departmentList" :fields="fields">
        <template #cell(createdAt)="row">
          {{ row.item.createdAt.substring(0, 10) }}
        </template>
        <template #cell(updateBtn)="row">
          <b-button size="sm" variant="success" @click="onClickEdit(row.item.id)">수정</b-button>
        </template>
        <template #cell(deleteBtn)="row">
          <b-button size="sm" variant="danger" @click="onClickDelete(row.item.id)">삭제</b-button>
        </template>
      </b-table>
    </div>

    <!-- inform 영역 -->
    <inform />
  </div>
</template>

<script>
import inform from './inform.vue'

export default {
  components: {
    inform: inform
  },
  data() {
    return {
      fields: [
        { key: 'id', label: 'id' },
        { key: 'name', label: '부서명' },
        { key: 'code', label: '부서코드' },
        { key: 'createdAt', label: '생성일' },
        { key: 'updateBtn', label: '수정' },
        { key: 'deleteBtn', label: '삭제' }
      ]
    }
  },
  computed: {
    departmentList() {
      return this.$store.getters.DepartmentList
    },
    insertedResult() {
      return this.$store.getters.DepartmentInsertedResult
    },
    updatedResult() {
      return this.$store.getters.DepartmentUpdatedResult
    },
    deletedResult() {
      return this.$store.getters.DepartmentDeletedResult
    }
  },
  watch: {
    insertedResult(value) {
      // 등록 후 처리

      if (value !== null) {
        if (value > 0) {
          // 등록이 성공한 경우

          // 1. 메세지 출력
          this.$bvToast.toast('등록 되었습니다.', {
            title: 'SUCCESS',
            variant: 'success',
            solid: true
          })

          // 2. 리스트 재 검색
          this.searchDepartmentList()
        } else {
          // 등록이 실패한 경우
          this.$bvToast.toast('등록이 실패하였습니다.', {
            title: 'ERROR',
            variant: 'danger',
            solid: true
          })
        }
      }
    },
    updatedResult(value) {
      // 수정 후 처리
      if (value !== null) {
        if (value > 0) {
          // 수정이 성공한 경우

          // 1. 메세지 출력
          this.$bvToast.toast('수정 되었습니다.', {
            title: 'SUCCESS',
            variant: 'success',
            solid: true
          })

          // 2. 리스트 재 검색
          this.searchDepartmentList()
        } else {
          // 수정이 실패한 경우
          this.$bvToast.toast('수정이 실패하였습니다.', {
            title: 'ERROR',
            variant: 'danger',
            solid: true
          })
        }
      }
    },
    deletedResult(value) {
      // 삭제 후 처리
      if (value !== null) {
        if (value > 0) {
          // 삭제가 성공한 경우

          // 1. 메세지 출력
          this.$bvToast.toast('삭제 되었습니다.', {
            title: 'SUCCESS',
            variant: 'success',
            solid: true
          })

          // 2. 리스트 재 검색
          this.searchDepartmentList()
        } else {
          // 삭제가 실패한 경우
          this.$bvToast.toast('삭제가 실패하였습니다.', {
            title: 'ERROR',
            variant: 'danger',
            solid: true
          })
        }
      }
    }
  },
  created() {
    this.searchDepartmentList()
  },
  methods: {
    searchDepartmentList() {
      this.$store.dispatch('actDepartmentList')
    },
    onClickAddNew() {
      // 신규등록

      // 1. 입력모드 설정
      this.$store.dispatch('actDepartmentInputMode', 'insert')

      // 2. 상세정보 초기화
      this.$store.dispatch('actDepartmentInit')

      // 3. 모달 출력
      this.$bvModal.show('modal-department-inform')
    },
    onClickEdit(id) {
      // (수정을 위한)상세정보

      // 1. 입력모드 설정
      this.$store.dispatch('actDepartmentInputMode', 'update')

      // 2. 상세정보 호출
      this.$store.dispatch('actDepartmentInfo', id)

      // 3. 모달 출력
      this.$bvModal.show('modal-department-inform')
    },
    onClickDelete(id) {
      // 삭제
      this.$bvModal.msgBoxConfirm('삭제 하시겠습니까?').then(value => {
        if (value) {
          this.$store.dispatch('actDepartmentDelete', id)
        }
      })
    }
  }
}
</script>
```

`[삭제]`버튼 클릭 시 `this.$bvModal.msgBoxConfirm`모달을 띄운다.(confirm역할을 하는 모달)
`Api`를 연결하면 실제 삭제 처리를 확인할 수 있다. 

**참고** `loading`중인 상황을 표시하기 위해서는 각 상황별(리스트 조회, 등록, 상세정보 조회, 수정, 삭제)로 `loading`변수를 Store에 준비해야 한다. 또한 각 화면에 로딩중임을 표시하는 영역을 만들어야 한다. 본 과정에서는 `loading`으로 인한 코드의 복잡성을 피하기 위해 생략했다. 각자 만들어 보는 것을 추천 한다.


### 사용자 관리 화면 제작
위와 같은 방법으로 **사용자 관리** 화면을 작성해 보자.

사용자 테이블은 다음과 같다. (`department_id`는 `FK`로써 부서테이블의 `PK`(`department.id`)와 Join된다.)
**user**
|속성명|필드명|타입|
|------|---|---|
|pk|id|int|
|부서PK|department_id|int|
|이름|name|varchar(100)|
|아이디|userid|varchar(255)|
|비밀번호|password|varchar(500)|
|사용자권한|role|varchar(20)|
|이메일|email|varchar(255)|
|전화번호|phone|varchar(255)|
|비밀번호 변경일|updated_pw_date|datetime|
|등록일시|created_at|datetime|
|수정일시|updated_at|datetime|
|삭제일시|deleted_at|datetime|

##### 1) Store 파일 생성
`department`파일을 참고하여 `user`의 `store`파일을 다음의 위치에 생성 해 볼 것.

> /src/store/models/user.js

**참고** 테스트용 데이터는 아래와 같이 사용 한다.

```javascript
/* 테스트 데이터 세팅 */
const UserList = [
  {
    id: 1,
    departmentId: 1,
    name: '홍길동',
    userid: 'hong',
    role: 'leader',
    email: 'hong@email.com',
    phone: '010-1234-5678',
    createdAt: '2021-12-01T00:00:00.000Z',
    Department: { id: 1, name: '개발팀', code: 'dev', createdAt: '2021-12-01T00:00:00.000Z' }
  },
  {
    id: 2,
    departmentId: 2,
    name: '김길동',
    userid: 'kim',
    role: 'member',
    email: 'kim@email.com',
    phone: '010-9876-5432',
    createdAt: '2021-12-01T00:00:00.000Z',
    Department: { id: 2, name: '영업팀', code: 'sales', createdAt: '2021-12-01T00:00:00.000Z' }
  }
]
```

##### 2) inform파일 생성
`department`파일을 참고하여 `user`의 `inform.vue`파일을 다음의 위치에 생성 해 볼 것.

> /src/views/user/inform.vue

User항목은 다음과 같다.
```javascript
...
export default {
  data() {
    return {
      user: {
        id: null,
        departmentId: null,
        name: null,
        userid: null,
        password: null,
        role: null,
        email: null,
        phone: null,
        updatedPwDate: null,
        createdAt: null
      },
...
```

모든 필드는 그냥 `input text`로 구현 하도록 한다.


##### 3) 리스트 화면(index.vue) 파일 생성
`department`파일을 참고하여 `user`의 `index.vue`파일을 다음의 위치에 생성 해 볼 것.

> /src/views/user/index.vue

출력할 필드는 다음과 같다.
```javascript
export default {
  ...
  data() {
    return {
      fields: [
        { key: 'id', label: 'id' },
        { key: 'name', label: '이름' },
        { key: 'Department', label: '부서' },
        { key: 'userid', label: '아이디' },
        { key: 'role', label: '권한' },
        { key: 'email', label: '이메일' },
        { key: 'createdAt', label: '생성일' },
        { key: 'updateBtn', label: '수정' },
        { key: 'deleteBtn', label: '삭제' }
      ]
    }
  },
  ...
```


#### 사용자의 권한(role) 기능
사용자의 권한은 다음과 같다.
  - 팀장: `leader`
  - 팀원: `member` (기본값)

사용자의 권한을 선택할 수 있도록 입력 폼을 바꿔보자. 
권한 입력 폼은`radio`로 구현하며 권한 값은 하드코딩 한다.

입력 폼 파일에서 다음과 같이 구현 한다.
> /src/views/user/inform.vue

##### 1) 권한 값 정의
```javascript
userRole: {
  default: 'member', // 기본값
  options: [
    { value: 'leader', text: '팀장' },
    { value: 'member', text: '팀원' }
  ]
}
```

신규등록인 경우 기본값을 세팅해주기 위해 아래와 같은 로직이 추가 된다.
```javascript
watch: {
  // 모달이 열린 이후에 감지됨
  infoData(value) {
    this.user = { ...value }

    this.setDefaultValues() // 기본값 세팅
  }
},
created() {
  // 모달이 최초 열릴때 감지됨
  this.user = { ...this.infoData }

  this.setDefaultValues() // 기본값 세팅
},
methods: {
  ...
  setDefaultValues() {
    // 기본값 세팅
    if (this.inputMode === 'insert') {
      this.user.role = this.userRole.default // 사용자 권한
    }
  }
  ...
}
```

**참고** 기본값을 세팅하는 방법은 Store에서 세팅할 수도 있고 vue파일에서 세팅할 수도 있다. 하나의 방법을 선택해서 통일성 있게 사용해야 한다.


##### 2) radio 버튼 구현
이제 권한 필드를 radio로 변경해 본다.
```html
<b-form-group label="권한" label-for="auth" label-cols="3">
  <b-form-radio-group id="auth" v-model="user.role" :options="userRole.options" />
</b-form-group>
```

#### 사용자의 소속 부서 연동
사용자 입력 폼에서 소속부서 선택은 `<select>`로 구현 해야 한다.

이를 위해서는 다음의 두가지 조건을 만족 해야 한다.
**사용자 등록 시** 부서 정보는 실제 부서리스트를 조회하여 나타내야 한다.
**사용자 수정 시** 부서 정보는 해당 사용자가 소속한 부서가 자동으로 선택된 상태이어야 하며 다른 부서로 변동할 수 있어야 한다.

##### 1) 부서정보 조회 하기
`created`에서  부서리스트를 조회 한다.
> /src/views/user/inform.vue
```javascript
...
  computed: {
    ...
    departmentList() {
      // 부서정보 출력
      return this.$store.getters.DepartmentList
    }
  },
  ...
  created() {
    // 모달이 최초 열릴때 감지됨
    this.user = { ...this.infoData }

    this.setDefaultValues() // 기본값 세팅

    this.$store.dispatch('actDepartmentList') // 부서정보 조회
  },
...
```

##### 2) select 구현하기
부서 입력폼을 selectBox로 다음과 같이 변경 한다.

> /src/vuews/user/inform.vue
```html
...
<b-form-group label="부서" label-for="department" label-cols="3">
  <b-form-select
    id="department"
    v-model="user.departmentId"
    :options="departmentList"
    value-field="id"
    text-field="name"
  >
    <template #first>
      <b-form-select-option :value="null">-- 부서를 선택해 주세요 --</b-form-select-option>
    </template>
  </b-form-select>
</b-form-group>
...
```

- `id`값을 `value`로 매핑하기 위해 `value-field="id"`로 처리하였다.
- `name`값을 `option`으로 매핑하기 `text-field="name"`로 처리하였다.
- `departmentId: null`인 경우의 처리를 위해 `<template #first>`부분에 `null`처리를 하였다.
- `v-model`을 통해 `selected`가 처리 된다. (수정 모드인 경우 자동으로 선택 되는지 확인 할 것)

#### 사용자의 비밀번호 기능

- 비밀번호는 `inputMode === 'insert'`인 경우에만 출력 한다.
- 비밀번호 입력 타입은 `password`로 변경 한다.
- `inputMode === 'update'`인 경우는 `[비밀번호 변경]`버튼만 출력 한다. (기능 구현은 안함)

##### 비밀번호를 입력받는 항목은 다음과 같은 기능이 필요하다
- "비밀번호"와 "비밀번호 확인"을 입력 받고 두 값이 같을 때에만 submit을 허용 한다.(`vuelidate`를 통해 구현 가능)
- "비밀번호"에 입력되는 값은 특정한 비밀번호 규칙(예: 대문자+소문자+특수문자+숫자 조합)을 만족해야만 한다.(`password-validator`를 통해 구현 가능)
- 여기에서는 구현하지 않고 추후 각자 구현해 보도록 한다.

### 장비 관리 화면 제작
마지막으로 **장비 관리**화면을 제작해 보자.
(샘플 소스에는 `name`과 `model`필드만 작성되어 있으니 나머지 필드를 추가해서 완성해 볼 것)

파일 작성 순서: device.js(Store) --> inform.vue(입력 폼) --> index.vue(리스트 화면)
(파일의 기본 틀을 잡아 놓고 각 기능별로 구현 하는 방법을 사용 하도록 한다.)


## 로그인
로그인/아웃 처리는 `jwt`를 발행/폐기 하는 방식으로 처리 한다.
발급된 토큰정보는 웹브라우저의 `localStorage`에 저장한다. 
백엔드 서버에 전송할때 토큰은 `request.headers.token`에 전송 한다. (백엔드의 API를 확인할 것)
응답 받을때 토큰은 `response.headers.token`에 전송 받는다. (백엔드의 API를 확인할 것)

**참고** 우리는 별도의 헤더 정보를 사용하며 `Bearer`를 사용하지 않는다.

### 로그인 화면
로그인 화면은 상단의 `app-header`부분 없이 독립된 디자인의 페이지로 생성하도록 한다.

##### 1) 로그인용 index.vue 파일 생성
라우터를 처리할 `index.vue`파일을 생성 한다.

> /src/views/auth/index.vue
```html
<template>
  <router-view />
</template>
```

##### 2) 로그인 페이지 생성
로그인용 빈페이지를 하나 생성 한다.

> /src/views/auth/login.vue
```html
<template>
  <div>
    <h1>로그인</h1>
  </div>
</template>

<script>
export default {}
</script>
```

##### 3) 라우터 등록
로그인 라우터는 `path: '/'`와 `path: '*'`사이에 (같은 동급으로)생성하도록 한다.
(`path`는 `/auth`를 사용 하자.)

> /src/router/index.js
```javascript
...
const routes = [
  {
    path: '/',
    component: () => import('../views'),
    redirect: '/home',
    children: [
      ...
    ]
  },
  {
    path: '/auth',
    component: () => import('../views/auth'),
    children: [
      {
        path: '/auth/login',
        component: () => import('../views/auth/login'),
        meta: { header: false }
      }
    ]
  },
  {
    path: '*',
    component: () => import('../components/NotFound.vue')
  }
]
...
```
로그인 주소는 `/auth/login`으로 한다.

##### 4) App.vue에서 헤더 제외
위에 등록한 `meta: { header: false }`를 통해 로그인 페이지에서는 헤더를 제거할 수 있다.
> /src/App.vue
```html
<template>
  <div>
    <app-header v-if="this.$route.meta.header !== false" />
    <router-view />
  </div>
</template>

<script>
import Header from './components/layout/Header'

export default {
  components: {
    'app-header': Header
  }
}
</script>

<style src="./assets/style/main.css"></style>
```
`<app-header v-if="this.$route.meta.header !== false" />`구문을 통해 `meta.header`값이 명백히 `false`인 경우에만 헤더를 제거할 수 있도록 하였다. (`meta.header`값이 `null` or `true`인 경우에는 헤더가 노출 된다.)

`http://localhost:8080/auth/login`에 접속해보면 헤더가 제거된 로그인 화면을 확인할 수 있다.

##### 5) 로그인 화면 생성
위에서 만든 로그인 페이지를 아이디/패스워드를 입력받는 화면으로 만들어 보자. (기능 제외)
>  /src/views/auth/login.vue
```html
<template>
  <div>
    <div style="margin-top: 80px">
      <b-row align-h="center">
        <b-col cols="4">
          <b-card title="로그인">
            <b-form-group label-cols="4" label-cols-lg="3" label="아이디" label-for="input-userid">
              <b-form-input id="input-userid" v-model="userid"></b-form-input>
            </b-form-group>
            <b-form-group label-cols="4" label-cols-lg="3" label="패스워드" label-for="input-password">
              <b-form-input id="input-password" v-model="password" type="password"></b-form-input>
            </b-form-group>
            <b-form-group label-cols="4" label-cols-lg="3" label="">
              <b-button variant="primary" @click="onSubmit">로그인</b-button>
            </b-form-group>
          </b-card>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userid: null,
      password: null
    }
  },
  methods: {
    onSubmit() {
      console.log('onSubmit', this.userid, this.password)
    }
  }
}
</script>
```

### 토큰 발행
`[로그인]`버튼 클릭 시 동작시킬 Store파일을 만들어 보자.

##### 1) jwt-decode 설치
발급된 토큰의 정보를 확인하기 위해 `jwt-decode`를 설치 한다.

```console
> npm install jwt-decode
```

##### 2) auth 스토어 생성
토큰 처리를 위한 `auth`스토어를 생성 한다.
> /src/store/models/auth.js
```javascript
import api from '../apiUtil'
import jwtDecode from 'jwt-decode'

/*
  테스트용 토큰
  {
    "id": 1,
    "userid": "hong",
    "name": "홍길동",
    "role": "leader",
    "iat": 1639466985,
    "exp": 1954826985
  }
  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwidXNlcmlkIjoiaG9uZyIsIm5hbWUiOiLtmY3quLjrj5kiLCJyb2xlIjoibGVhZGVyIiwiaWF0IjoxNjM5NDY2OTg1LCJleHAiOjE5NTQ4MjY5ODV9.-hTy681tbe62pV9tjArzc5Ig33frnh9j_NjegGiHJNw
*/
const testToken =
  'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwidXNlcmlkIjoiaG9uZyIsIm5hbWUiOiLtmY3quLjrj5kiLCJyb2xlIjoibGVhZGVyIiwiaWF0IjoxNjM5NDY2OTg1LCJleHAiOjE5NTQ4MjY5ODV9.-hTy681tbe62pV9tjArzc5Ig33frnh9j_NjegGiHJNw'

const stateInit = {
  TokenUser: {
    id: null,
    userid: null,
    name: null,
    role: null,
    iat: null,
    exp: null
  }
}

export default {
  state: {
    TokenUser: { ...stateInit.TokenUser }, // token에서 추출한 사용자 정보
    Loading: false,
    Error: null
  },
  getters: {
    TokenUser: state => state.TokenUser,
    TokenLoading: state => state.Loading,
    TokenError: state => state.Error
  },
  mutations: {
    setTokenUser(state, data) {
      state.TokenUser = data
    },
    setLoading(state, data) {
      state.Loading = data
      state.Error = null
    },
    setError(state, data) {
      state.Error = data
      state.Loading = false
      state.TokenUser = { ...stateInit.TokenUser }
    },
    clearError(state) {
      state.Error = null
    }
  },
  actions: {
    authLogin(context, payload) {
      // 로그인 처리

      // 상태값 초기화
      context.commit('clearError')
      context.commit('setLoading', true)

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        const token = testToken
        const decodedToken = jwtDecode(token)

        // api를 호출하지 않으므로 직접 localStorage에 token을 저장 한다.
        window.localStorage.setItem('token', token)

        context.commit('setLoading', false)
        context.commit('setTokenUser', decodedToken)
      }, 2000) // 처리 시간을 2초로 주었다.

      /* RestApi 호출 */
      /*
      api
        .post('/serverApi/auths/token', payload)
        .then(response => {
          const token = response.headers.token
          const decodedToken = jwtDecode(token)

          // 정상인 경우 처리
          context.commit('setLoading', false)
          context.commit('setTokenUser', decodedToken)
        })
        .catch(error => {
          // 에러인 경우 처리
          context.commit('setLoading', false)
          context.commit('setError', error)
        })
      */
    }
  }
}
```

##### 3) axios의 interceptor 활용
`axios`에서 제공하는 `interceptors`를 이용하여 `request`와 `response`할때 `headers`에 `token`값을 전송/수신 할 수 있다.
**주의** 토큰 정보를 헤더를 통해서 백엔드와 주고 받을 때에는 백엔드의 API와 맞춰야 한다.

> /src/store/apiUtil.js
```javascript
import axios from 'axios'

const api = axios.create()

// request(요청)시 아래의 로직이 인터셉트 된다.
api.interceptors.request.use(
  async request => {
    // header.token 전송
    const token = window.localStorage.getItem('token')
    request.headers.token = token

    return request
  },
  async error => {
    return Promise.reject(error)
  }
)

// response(응답)시 아래의 로직이 인터셉트 된다.
api.interceptors.response.use(
  async response => {
    // header.token 자동 갱신
    const token = response.headers.token // token을 header에서 받은 경우
    if (token) {
      window.localStorage.setItem('token', token)
    }
  },
  async error => {
    return Promise.reject(error)
  }
)

export default api
```
`api.interceptors`를 잘 눈여겨 보도록 하자.

##### 4) store index.vue 등록
store의 `index.vue`에 등록한다. (`Auth`등록은 맨 위에 하자)
> /src/store/index.js
```javascript
import Vue from 'vue'
import Vuex from 'vuex'
import Auth from './models/auth'
import Department from './models/department'
import User from './models/user'
import Device from './models/device'

Vue.use(Vuex)

export default new Vuex.Store({
  modules: {
    Auth,
    Department,
    User,
    Device
  }
})
```

##### 5) 로그인 페이지 완성
로그인 페이지를 완성해 보자.
> /src/views/auth/login.vue
```html
<template>
  <div>
    <div style="margin-top: 80px">
      <b-row align-h="center">
        <b-col cols="4">
          <b-card title="로그인">
            <b-form-group label-cols="4" label-cols-lg="3" label="아이디" label-for="input-userid">
              <b-form-input id="input-userid" v-model="userid"></b-form-input>
            </b-form-group>
            <b-form-group label-cols="4" label-cols-lg="3" label="패스워드" label-for="input-password">
              <b-form-input id="input-password" v-model="password" type="password"></b-form-input>
            </b-form-group>
            <b-form-group label-cols="4" label-cols-lg="3" label="">
              <b-button variant="primary" :disabled="loading" @click="onSubmit"
                ><b-spinner v-if="loading" small></b-spinner> 로그인</b-button
              >
            </b-form-group>
          </b-card>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import jwtDecode from 'jwt-decode'

export default {
  data() {
    return {
      userid: null,
      password: null
    }
  },
  computed: {
    tokenUser() {
      return this.$store.getters.TokenUser
    },
    loading() {
      return this.$store.getters.TokenLoading
    },
    error() {
      return this.$store.getters.TokenError
    }
  },
  watch: {
    tokenUser(value) {
      if (value && value.id && value.id > 0) {
        // 로그인이 완료된 상황
        this.$router.push('/home') // 메인 페이지 이동
      }
    },
    error(errValue) {
      if (errValue !== null) {
        // 메세지 출력
        this.$bvToast.toast('아이디/비밀번호를 확인해 주세요.', {
          title: '로그인 에러',
          variant: 'danger',
          solid: true
        })
      }
    }
  },
  created() {
    // 이미 토큰을 가지고 있는 경우 처리를 위한 로직
    const token = window.localStorage.getItem('token')
    if (token) {
      const decodedToken = jwtDecode(token)
      const today = new Date()
      const expDate = new Date(decodedToken.exp * 1000)

      if (expDate && expDate >= today) {
        // 토큰이 유효한 경우
        this.$router.push('/home') // 메인 페이지 이동
      } else {
        // 토큰이 만료된 경우
        window.localStorage.removeItem('token') // 토큰 삭제
      }
    }
  },
  methods: {
    onSubmit() {
      this.$store.dispatch('authLogin', { userid: this.userid, password: this.password })
    }
  }
}
</script>
```
`[로그인]`버튼에 loading 기능이 구현 되었다. (로그인 하는 동안 버튼이 spin됨)
**주의** 로그인이 실패한 경우 아이디나 비밀번호중 어느 것이 잘못되었는지 알려주지 않도록 한다. (보안에 유의)

### 로그인 테스트

- 로그인 페이지(`/auth/login`) 접속 확인
- 로그인 후 `/home`페이지로 이동하는지 확인
- 로그인 후 `localStorage`에 `token`이 저장되는지 확인
  - 웹브라우저의 개발자도구에서 `Application > Storage > Local Storage`에서 찾을 수 있다.
  - 해당 토큰을 삭제하면 로그아웃이 된걸로 간주 된다.
- 토큰을 보유한 상태에서 로그인 페이지(`/auth/login`)로 접속 시 메인 페이지(`/home`)로 리다이렉트 되는지 확인
- 만료된 토큰을 보유한 상태에서 로그인 페이지(`/auth/login`)로 접속 시 로그인 페이지가 유지되는지 확인
  - 메인 페이지`/home`로 가면 안됨
- 로그인 상태에서 페이지 `reload`를 해보자.
  - 토큰정보는 `localStorage`에 남아있는데 Store에 저장된 `TokenUser`정보는 없어진 것을 확인할 수 있다. 
  - 이 문제는 토큰검사에서 해결하도록 한다.

### 토큰 폐기
토큰 폐기를 통해 로그아웃 기능을 구현할 수 있다.

보통 로그아웃을 함수로만 구현하는데 우리는 실제 페이지를 만들어서 해당 페이지에서 처리하도록 하자.
(로그아웃 페이지를 만들면 url을 통한 강제 로그아웃 처리가 가능하다.)

##### 1) store에서 토큰폐기 로직 생성
> /src/store/models/auth.js
```javascript
...
export default {
  ...
  mutations: {
    ...
    setLogout(state) {
      state.Loading = false
      state.Error = null
      state.TokenUser = { ...stateInit.TokenUser }
    }
  },
  actions: {
    authLogin(context, payload) {
      ...
    },
    async authLogout(context) {
      // 로그아웃 처리
      
      // 상태값 초기화
      context.commit('clearError')
      context.commit('setLoading', true)

      /* 테스트 데이터 세팅 */
      setTimeout(() => {
        context.commit('setLogout') // 로그아웃 처리
        window.localStorage.removeItem('token') // 토큰 삭제
      }, 2000) // 처리 시간을 2초로 주었다.

      /* RestApi 호출 */
      // api 결과와 관계없이 로컬에서는 로그아웃 처리 함
      /*
      try {
        await api.delete('/serverApi/auths/token') // await를 걸지 않으면 토큰삭제 후 전송될 수 있음
        context.commit('setLogout') // 로그아웃 처리
        window.localStorage.removeItem('token') // 토큰 삭제
      } catch (err) {
        context.commit('setLogout') // 로그아웃 처리
        window.localStorage.removeItem('token') // 토큰 삭제
      }
      */
    }
  }
}
```
`mutations`에 로그아웃을 한번에 처리하는 `setLogout`을 추가하였다.
상용 서비스에서 로그인을 처리하는 백엔드를 호출할때는 반드시 `https`를 사용해야 한다.


##### 2) 로그아웃 페이지 생성
로그아웃을 처리하는 빈페이지를 생성해 보자.
> /src/views/auth/logout.vue
```html
<template>
  <div>
    <div class="text-center" style="margin-top: 200px">
      <b-spinner variant="secondary" style="width: 3rem; height: 3rem" label="Logout..."></b-spinner>
    </div>
  </div>
</template>

<script>
export default {}
</script>
```
라우터 주소는 `/auth/logout`으로 한다.
로그아웃 페이지에 접속하면 스핀되는 이미지를 볼 수 있을 것이다. 
로그아웃이 처리되는 동안 보여줄 이미지가 있으면 이곳에 넣으면 된다.

##### 3) 로그아웃 기능 넣기
로그아웃 기능을 넣어 보자.
> /src/views/auth/logout.vue
```html
<template>
  <div>
    <div class="text-center" style="margin-top: 200px">
      <b-spinner variant="secondary" style="width: 3rem; height: 3rem" label="Logout..."></b-spinner>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    loading() {
      return this.$store.getters.TokenLoading
    }
  },
  watch: {
    loading(value) {
      if (value === false) {
        // 로그아웃 처리 후 이동
        this.$router.push('/auth/login')
      }
    }
  },
  created() {
    this.$store.dispatch('authLogout')
  }
}
</script>
```

##### 4) header에서 로그아웃 링크 걸기
header파일에서 로그인했을 경우 해당 사용자 이름을 출력해주고
이름을 클릭하면 드롭다운에서 로그아웃 링크를 걸어주도록 하자.

> /src/components/layout/Header.vue
```html
<template>
  <div>
    <b-navbar toggleable="lg" type="light" style="border-bottom: 1px solid rgba(0, 0, 0, 0.1)">
      <b-navbar-brand href="/">VUEPROJ</b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">메뉴1</b-nav-item>
          <b-nav-item href="#">메뉴2</b-nav-item>
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav v-if="isLoggedin" class="ml-auto">
          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template #button-content>
              <em>{{ tokenUserName }}</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#" @click="onClick('/auth/logout')">Log Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  computed: {
    isLoggedin() {
      let login = false
      if (this.$store.getters.TokenUser && this.$store.getters.TokenUser.id > 0) {
        login = true
      }

      return login
    },
    tokenUserName() {
      return this.$store.getters.TokenUser && this.$store.getters.TokenUser.name
    }
  },
  methods: {
    onClick(path) {
      this.$router.push(path)
    }
  }
}
</script>
```


### 토큰 검사
`SPA`의 특징중 하나는 페이지를 새로고침하게되면 모든 Store정보가 날아간다는 것이다.
따라서 ***로그인한 사용자 정보*** 같이 중요한 Store정보는 계속 유지 할 수 있도록 해야 한다.
(`localStorage`의 정보는 날아가지 않는다. (컴퓨터를 재부팅 해도 유지됨. 보안에 유의!!))

토큰 검사는 router의 `beforeEach`를 이용해서 구현 한다. 
라우팅 시 페이지 이동하기 전에 체크하는 로직을 구현할 수 있다.

`router.beforeEach`는 반드시 `const router = new Router`의 하단에 위치해야 한다.
자세한 router사용법은 공식 문서를 참조할 것 (https://router.vuejs.org/kr/guide/advanced/navigation-guards.html)

> /src/router/index.js
```javascript
...
const routes = [
  {
    path: '/',
    ...
  },
  {
    path: '/auth',
    component: () => import('../views/auth'),
    children: [
      {
        path: '/auth/login',
        component: () => import('../views/auth/login'),
        meta: { header: false, noLogin: true }
      },
      {
        path: '/auth/logout',
        component: () => import('../views/auth/logout'),
        meta: { header: false, noLogin: true }
      }
    ]
  },
  {
    path: '*',
    component: () => import('../components/NotFound.vue'),
    meta: { header: false }
  }
]

const router = new VueRouter({
  mode: 'history',
  base: process.env.BASE_URL,
  routes
})

router.beforeEach(async (to, from, next) => {
  // console.log('router.beforeEach', to, from)

  const noLogin = to.meta.noLogin // 이동할 페이지에서 로그인 허용여부 확인

  if (noLogin === true) {
    // 로그인이 필요없는 페이지는 그냥 이동
    next()
  } else {
    // 로그인이 필요한 페이지는 토큰 체크 후 통과 여부 결정

    // 1. localStorage에서 토큰 추출
    const token = window.localStorage.getItem('token')

    // TODO: 리다이렉트 페이지 처리(이동하려던 페이지로 이동시킬 수 있다.)

    try {
      const decodedToken = jwtDecode(token) // 토큰디코딩
      const today = new Date() // 오늘날짜
      const expDate = new Date(decodedToken.exp * 1000) // 토큰에서 만료일추출

      if (expDate && expDate >= today) {
        // 토큰이 유효한 경우

        // 1. tokenUser정보가 없어진 경우 다시 갱신한다.
        const tokenUser = store.getters['TokenUser']
        if (!tokenUser || !tokenUser.id > 0) {
          store.dispatch('authTokenUser', token)
        }

        // 처리를 다 했으면 가던길 가자
        next()
      } else {
        // 토큰이 만료된 경우
        next('/auth/login') // 로그인 페이지로 이동(여기에서 토큰을 삭제해준다.)
      }
    } catch (err) {
      // 토큰 추출이 실패한 경우에 대한 처리
      next('/auth/login') // 로그인 페이지로 이동
    }
  }
})

export default router
```
로그인이 필요없는 페이지에 대해서 라우터에 메타정보(`noLogin=true`)를 넣어서 관리할 수 있도록 했다.


**참고**
페이지가 강제 리다이렉트 되면 `Error: Redirected when going from "/auth/login" to "/home" via a navigation guard.`라는 에러가 보인다. 이는 에러가 아니라 페이지가 리다이렉트 되었다고 알려주는 것이다.

### 로그인 테스트

- 로그아웃 상태에서
  - 로그인이 필요한 페이지(`/home`)로 이동했을때 로그인 페이지(`/auth/login`)로 리다이렉트 되는지 확인
  - 주소창에 로그아웃 페이지(`/auth/logout`)를 작성해서 이동시키면 로그인 페이지(`/auth/login`)로 이동하는지 확인
- 로그인 상태에서
  - 새로고침(F5)을 해도 로그인이 유지되는지 확인
  - 페이지 이동에 이상이 없는지 확인
  - 로그아웃이 정상적으로 이루어 지는지 확인
  - 주소창에 로그인 페이지(`/auth/login`)를 작성해서 이동시키면 홈화면(`/home`)으로 리다이렉트 되는지 확인
  - 주소창에 로그아웃 페이지(`/auth/logout`)를 작성해서 이동시키면 로그아웃이 된 후 로그인 페이지(`/auth/login`)로 이동하는지 확인
  - `localStorage`의 토큰을 삭제한 후 페이지 이동 시 로그인 페이지(`/auth/login`)로 이동하는지 확인
  - `localStorage`의 토큰을 삭제한 후 새로고침(F5)을 하면 로그인 페이지(`/auth/login`)로 이동하는지 확인
- 기타 버그를 찾아보라.


## MQTT
실시간 데이터 수집및 전달을 위해 mqtt를 사용해 보도록 한다.
mqtt를 위해 `mosquitto`를 사용 한다. (mosquitto는 Docker를 이용해서 구축 한다.)

### mosquitto 홈 디렉토리 설정
`mosquitto`의 도커관련 디렉토리 구조는 다음과 같다.

- 도커 볼륨 디렉토리: `/home/docker/volumes`
- 도커 컨테이너 디렉토리: `/home/docker/containers`

### mosquitto 환경 설정

환경 설정은 다음의 값만 설정하여 사용 한다.(나머지는 디폴트 값으로 사용)
파일 위치: `/home/docker/containers/mosquitto/mosquitto.conf`
> mosquitto.conf
```
...
# =================================================================
# Listeners
# =================================================================

# listen for mqtt on tcp
port 1883

# listen for websockets
listener 9001
protocol websockets

# =================================================================
# Security
# =================================================================
allow_anonymous true
...
```

### mosquitto 도커 컨테이너 실행
`mosquitto` 도커의 컨테이너 실행 파일은 다음과 같다.
파일 위치: `/home/docker/containers/mosquitto/dockerRun.sh`

> dockerRun.sh
```shell
#!/bin/bash

# setting - docker info
DOCKER_IMAGE_NAME=eclipse-mosquitto
DOCKER_IMAGE_TAG=2.0.10
DOCKER_CONTAINER_NAME=$DOCKER_IMAGE_NAME-dev
DOCKER_PORT_MQTT=1883
DOCKER_PORT_WEBSOCKET=9001
DOCKER_VOLUME=/home/docker/volumes/$DOCKER_CONTAINER_NAME
DOCKER_IMAGE=$DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG

# mosquitto config copy
mkdir -p $DOCKER_VOLUME/mosquitto/config
cp mosquitto.conf $DOCKER_VOLUME/mosquitto/config/mosquitto.conf

# docker run #################################
docker run --name $DOCKER_CONTAINER_NAME \
-p $DOCKER_PORT_MQTT:1883 \
-p $DOCKER_PORT_WEBSOCKET:9001 \
-v $DOCKER_VOLUME/mosquitto/config/mosquitto.conf:$DOCKER_HOME/config/mosquitto.conf \
-d \
$DOCKER_IMAGE
```
**참고** 도커 컨테이너를 띄운 후 포트 포워딩을 잊지 말 것!


#### 개발PC에 mqtt 설치하기
mqtt를 개발PC에서 테스트하기 위해서 다음과 같이 설치 한다.
```console
> npm install -g mqtt
```
`-g`옵션을 통해 글로벌로 설치하도록 한다.


#### mqtt 구독 테스트
다음의 명령어를 개발PC의 명령 프롬프트를 통해 실행 시키면 실시간 구독이 된다. (종료는 Ctrl-c)

```console
> mqtt subscribe -h 192.168.0.123 -p 1883 -t vueproj/testdata
```
**주의** ip부분에 본인 PC의 아이피를 세팅할 것 (127.0.0.1은 동작하지 않음)

토픽은 `vueproj/testdata`로 한다.

#### mqtt 발행 테스트
다음의 명령어를 통해 mqtt를 발행할 수 있다.(개발PC에서 실행 하도록 하자)

```console
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "test_abc_123"
```
mqtt를 발행하고 구독에 정보가 들어오는지 확인 한다.

#### 객체 데이터 전달 테스트
json객체를 전달하고자 할때는 json object를 string으로 변환한 후 발송해야 한다.

##### json object
```json
{ "data": { "model": 1, "data1": 100, "data2": "abc" } }
```
**팁:** 한 줄로 만들어야 `\n`값을 없앨 수 있다.

##### json string
위와 같은 json object를 다음과 같이 string으로 변환 한다.
```
"{ \"data\": { \"model\": 1, \"data1\": 100, \"data2\": \"abc\" } }"
```
**참고:** json to string 변환 온라인 서비스: https://tools.knowledgewalls.com/json-to-string


##### 3) mqtt 발행 테스트
다음과 같이 발행을 해보자
```console
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"data\": { \"model\": 1, \"data1\": 100, \"data2\": \"abc\" } }"
```
구독된 데이터가 원데이터와 맞는지 확인해 본다. (`{ "data": { "model": 1, "data1": 100, "data2": "abc" } }`)


#### mqtt 수신(in vue.js)
vue.js에서 mqtt를 수신해 보자.
웹브라우저에서는 mqtt를 그대로 수신할 수 없다. 따라서 `websocket`를 통해 수신하도록 한다.

##### mqtt client 설치
vue.js에서 사용할 mqtt 라이브러리를 설치 한다. (아래 내용은 현재 `vueproj`에서 사용할 npm이다. `package.json`에 설치 됨)

```console
> npm i mqtt
```
`mqtt`라이브러리에서 `websocket`수신이 가능하다. (별도의 `websocket`라이브러리 필요 없음)

##### mqtt 수신 코드 작성
보통 mqtt서버 연결에 대한 설정은 `.env`를 통해 이루어 진다.
> /.env
```
NODE_ENV=production
VUE_APP_SERVER=http://localhost:3000
VUE_APP_MQTT=ws://192.168.0.123:9001
```

대시보드에서 mqtt를 수신할 예정이므로 대시보드 파일을 열어서 다음과 같이 작성 한다.

> /src/views/dashboard/index.vue
```html
<template>
  <div>
    <h1>대시보드</h1>
    {{ mqttData }}
  </div>
</template>

<script>
import mqtt from 'mqtt'

export default {
  data() {
    return {
      mqttData: null
    }
  },
  created() {
    this.createMqtt()
  },
  methods: {
    createMqtt() {
      // mqtt연결
      const  mqttClient = mqtt.connect(process.env.VUE_APP_MQTT)

      mqttClient.on('connect', () => {
        // mqtt연결 시 구독한다.
        const topic = 'vueproj/testdata' // 구독할 topic
        mqttClient.subscribe(topic, {}, (error, res) => {
          if (error) {
            console.error('mqtt client error', error)
          }
        })
      })

      // 메세지 실시간 수신
      mqttClient.on('message', (topic, message) => {
        this.mqttData = JSON.parse(message) // json string으로만 받을 수 있음
      })
    }
  }
}
</script>
```
위와 같이 코드를 작성 후 다음과 같이 `mqtt`발행을 해보자.
```console
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"data\": { \"model\": 1, \"data1\": 100, \"data2\": \"abc\" } }"
```
대시보드 페이지에서 수신이 잘 되는지 확인해 보자. (json타입의 string으로 발송해야 수신할 수 있다.)

**참고** `console.error`는 제거하지 말 것! 


#### .env 설정시 주의 사항
`process.env.VUE_APP_MQTT`를 사용할때 `npm run build`를 해버리면 현재 설정된 값이 **하드코딩** 되어 버린다.
도커컨테이너에서 아무리 환경변수를 바꾸어 주어도 바뀌지 않는다.
이를 해결하기 위해서는 `.env`에 설정하지 말아야 한다.

백엔드인 `nodejs`는 `.env`의 설정값을 도커컨테이너 실행 시 변경이 가능하지만 (서버의 환경변수 적용 가능)
프론트엔드인 `vuejs`는 `.env`의 설정값을 도커컨테이너에서 변경이 불가능 하다. (서버의 환경변수 적용 불가)


## 차트 그리기
화면에 차트를 그려보자

#### 차트 설치
vue.js에서 사용할 차트 프로그램을 설치 한다. 
**참고** https://vue-chartjs.org/guide/

```console
> npm i vue-chartjs@3.5.1 chart.js@2.9.4
```
`vue-chartjs`와 `chart.js`의 버전이 맞아야 한다.(`chart.js`의 최신버전인 3.x버전은 동작하지 않음)

#### 차트 그리기

가장 단순한 Line-Chart를 그려보자.

##### 차트 컴포넌트 파일 생성
line-chart를 처리할 컴포넌트를 생성 한다.

> /src/components/chart/lineChart.js
```javascript
import { Line, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  extends: Line,
  mixins: [reactiveProp],
  props: ['options'],
  mounted() {
    // this.chartData is created in the mixin.
    // If you want to pass options please create a local options object
    this.renderChart(this.chartData, this.options)
  }
}
```

##### 화면에 차트 출력
대시보드 파일에서 차트를 출력해보자.
(가독성을 위해 mqtt 코드는 제거하고 차트관련 코드만 작성 하도록 한다.)

> /src/views/dashboard/index.vue
```html
<template>
  <div>
    <h1>대시보드</h1>
    <div v-if="chartData">
      <line-chart :chart-data="chartData" style="width: 600px"></line-chart>
    </div>
  </div>
</template>

<script>
import LineChart from '@/components/chart/lineChart'

export default {
  components: {
    'line-chart': LineChart
  },
  data() {
    return {
      chartData: null
    }
  },
  mounted() {
    this.makeChartData()
  },
  methods: {
    makeChartData() {
      this.chartData = {
        labels: ['1sec', '2sec', '3sec', '4sec', '5sec'],
        datasets: [
          {
            label: '장비1',
            data: [100, 120, 130, 150, 110]
          }
        ]
      }
    }
  }
}
</script>
```
화면을 확인해 보자.


## 대시보드 작업
실시간 데이터를 수집하여 대시보드에서 그래프를 그려보도록 한다.
실시간 데이터는 MQTT를 통해 수집하며 data의 흐름은 다음과 같다.
data --> MQTT --> websocket --> chart

#### 1) 데이터 정의
가상의 장비(Edge1)가 다음과 같은 데이터를 발생 시킨다고 간주 한다.

##### json object
```json
{
  "id": 1,
  "name": "Edge1",
  "model": "E001",
  "tag1": 100,
  "tag2": 30,
  "datetime": "2021-12-01T00:00:00.000Z"
}
```

##### json string
위의 object형태의 데이터를 mqtt로 전송하기 위해서 다음과 같이 string 형태로 변경 한다.
```
"{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 100, \"tag2\": 30, \"datetime\": \"2021-12-01T00:00:00.000Z\" }"
```

##### mqtt publish
cmd를 통해 다음과 같이 publish할 수 있다. (자동발생 프로그램을 만들면 편리하다)

```console
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 100, \"tag2\": 30, \"datetime\": \"2021-12-01T00:00:00.000Z\" }"
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 130, \"tag2\": 35, \"datetime\": \"2021-12-01T00:00:10.000Z\" }"
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 120, \"tag2\": 40, \"datetime\": \"2021-12-01T00:00:20.000Z\" }"
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 110, \"tag2\": 50, \"datetime\": \"2021-12-01T00:00:30.000Z\" }"
> mqtt publish -h 192.168.0.123 -p 1883 -t vueproj/testdata -m "{ \"id\": 1, \"name\": \"Edge1\", \"model\": \"E001\", \"tag1\": 100, \"tag2\": 20, \"datetime\": \"2021-12-01T00:00:40.000Z\" }"
```

#### 2) mqtt 수신하기(vue.js)
mqtt를 통해 발생된 데이터를 수신하고 차트용 데이터에 계속 추가 하도록 한다.
mqtt데이터 수신코드와 차트출력 코드를 결합해 본다.

> /src/views/dashboard/index.vue
```html
<template>
  <div>
    <h1>대시보드</h1>
    <div>장비: {{ selected.deviceName }}</div>
    <div>태그: {{ selected.tagList }}</div>
    <div v-if="chartData">
      <line-chart :chart-data="chartData" style="width: 500px"></line-chart>
    </div>
  </div>
</template>

<script>
import mqtt from 'mqtt'
import LineChart from '@/components/chart/lineChart'

export default {
  components: {
    'line-chart': LineChart
  },
  data() {
    return {
      selected: {
        // 선택된 장비 정보
        deviceId: 1, // TODO: 현재 화면에서 사용할 장비ID(선택 가능하도록 변경하도록 한다.)
        deviceName: 'Edge1', // TODO: 현재 화면에서 출력할 장비이름(deviceId선택 시 자동 세팅되도록 한다.)
        tagList: ['tag1', 'tag2'] // TODO: 현재 화면에서 출력할 태그 이름(deviceId선택 시 해당 장비의 태그를 설정할 수 있도록 한다.)
      },
      maxDataLength: 20, // TODO: 현재 차트에서 출력할 데이터의 최대크기(화면에서 입력 가능하도록 한다.)
      mqttDataList: [], // mqtt를 통해 받은 데이터(리스트로 계속 추가됨)
      chartData: null, // 차트로 표현될 데이터
      chartLabels: [], // 차트에서 사용할 라벨 리스트(가로축 라벨)
      chartDatasetLabels: [], // 차트에서 사용할 데이터셋 라벨 리스트
      chartDatasetDataList: [] // 차트에서 사용할 데이터셋 데이터 리스트
    }
  },
  created() {
    this.createMqtt()
  },
  mounted() {
    this.makeChartData()
  },
  methods: {
    createMqtt() {
      // mqtt연결
      const mqttClient = mqtt.connect(process.env.VUE_APP_MQTT)

      mqttClient.on('connect', () => {
        // mqtt연결 시 구독한다.
        const topic = 'vueproj/testdata' // 구독할 topic
        mqttClient.subscribe(topic, {}, (error, res) => {
          if (error) {
            console.error('mqtt client error', error)
          }
        })
      })

      // 메세지 실시간 수신
      mqttClient.on('message', (topic, message) => {
        const mqttData = JSON.parse(message) // json string으로만 받을 수 있음

        // 선택된 devicdId만 수용함
        if (this.selected.deviceId === mqttData.id) {
          this.removeOldData() // 오래된 데이터 제거

          this.mqttDataList.push(mqttData) // 리스트에 계속 추가함

          this.makeChartLabels(mqttData) // 차트라벨 생성
          this.makeChartData() // 차트용 데이터 작성
        }
      })
    },
    removeOldData() {
      // 현재 차트에 출력할 수가 x개를 넘어서면 제일 오래된 데이터를 제거 한다.
      if (this.maxDataLength - 1 < this.mqttDataList.length) {
        this.mqttDataList.shift() // mqttData제거
        this.chartLabels.shift() // 차트라벨 제거
      }
    },
    makeChartData() {
      // 차트용 데이터 생성

      // mqtt정보가 없으면 기본 그래프를 그려준다.(이것이 없으면 그래프 자체가 나오지 않음)
      if (this.mqttDataList.length === 0) {
        this.chartData = {
          labels: ['0'],
          datasets: [
            {
              label: 'no data',
              data: [0]
            }
          ]
        }

        return
      }

      // 데이터셋 라벨 리스트 생성(태그 리스트(tagList)를 데이터셋 라벨로 사용한다.)
      const datasetLabels = []
      for (let i = 0; i < this.selected.tagList.length; i += 1) {
        const tagName = this.selected.tagList[i] // tagName을 추출함
        datasetLabels.push(tagName) // tagName을 라벨로 사용함
      }
      this.chartDatasetLabels = Array.from(new Set(datasetLabels)) // 중복 제거

      // 차트 데이터 생성
      this.chartData = {
        labels: this.chartLabels,
        datasets: this.makeDatasetDatas()
      }
    },
    makeChartLabels(mqttData) {
      // 차트라벨(가로측) 생성
      this.chartLabels.push(mqttData.datetime.substring(14, 19)) // datetime을 사용한다.(분:초만 추출함)
    },
    makeDatasetDatas() {
      // 데이터셋의 데이터 추출
      const datasetDatas = []

      for (let i = 0; i < this.chartDatasetLabels.length; i += 1) {
        const label = this.chartDatasetLabels[i] // label을 하나씩 추출한다.
        const datas = [] // 해당 label에 속한 데이터셋의 데이터 리스트

        // mqtt로 들어온 데이터에서 key값으로 사용된 tag와 현재 label이 같으면 해당 데이터를 추출 한다.
        for (let j = 0; j < this.mqttDataList.length; j += 1) {
          const mqttData = this.mqttDataList[j]
          const tagData = mqttData[label] // 현재 데이터셋 label과 같은 태그만 추출한다.
          datas.push(tagData)
        }

        datasetDatas.push({
          label: label,
          data: datas
        })
      }

      return datasetDatas
    }
  }
}
</script>
```

테스트 방법은 mqtt publish를 명령어로 호출하여 실시간 그래프가 그려지는지 확인 한다.


#### 3) TODO처리하기
- 대시보드에서 장비를 선택해서 해당 장비의 상태를 모니터링 할 수 있도록 해보자.
  - `<select`사용, 선택하면 곧바로 변경해줄 것(버튼 사용X)
  - 장비관리에서 등록한 실제 장비내용으로 선택할 수 있어야 한다.
- 차트에서 출력할 데이터 수(`maxDataLength`)를 화면에서 선택할 수 있도록 해보자.
  - `<select` 사용, `option`은 20, 30, 50, 100으로 고정, 기본값은 20
- 데이터 생성기를 만들어 보자
  - 가상의 장비를 nodejs로 만들어서 데이터를 주기적으로 생성할 수 있도록 하자.
  - `setInterval`함수 사용


## Docker

지금까지 만든 소스를 Docker환경에서 띄워보자.

### 도커 관련 파일 생성
도커 이미지를 생성하기 위해서는 `Dockerfile`파일을 생성해야 한다.
`vueproj`프로젝트 내에서 다음의 파일들을 생성한다.

##### 1) Dockerfile 생성
`nginx`를 기반으로 하는 `Dockerfile`을 다음과 같이 생성 한다.

> /Dockerfile
```
FROM nginx:1.19

# set locale
RUN apt-get update \
    && apt-get install -y vim \
    && apt-get install -y locales
RUN sed -i 's/^# \(ko_KR.UTF-8\)/\1/' /etc/locale.gen
RUN localedef -f UTF-8 -i ko_KR ko_KR.UTF-8
ENV LC_ALL ko_KR.UTF-8

# install node.js
ENV NVM_VERSION v0.34.0
ENV NODE_VERSION 14.15.5
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN apt-get -y install curl build-essential
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/${NVM_VERSION}/install.sh | bash
RUN source ~/.nvm/nvm.sh; \
    nvm install $NODE_VERSION; \
    nvm use --delete-prefix $NODE_VERSION;
ENV PATH /root/.nvm/versions/node/v$NODE_VERSION/bin:$PATH

# install home
RUN mkdir -p /home/www
COPY . /home/www
WORKDIR /home/www

# make build && delete source files
RUN npm install \
    && npm run build \
    && rm -rf $(ls | grep -v dist)

# nginx config
COPY nginx-default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
```

- 도커내에서의 홈 디렉토리는 `/home/www`로 설정 하였다.
- `npm run build`이후 `dist`폴더의 파일만 남기고 모두 삭제(`rm -rf $(ls | grep -v dist)`)하여 공간을 절약하였다.
  - 빌드가 되면 `node_modules`는 쓰이지 않는다.(용량이 가장 큼)
  - 빌드된 파일은 `/home/www/dist`에 생성 된다.
- 현재 페이지의 `nginx-default.conf`파일을 도커내의 `/etc/nginx/conf.d/default.conf`로 카피하도록 하였다.


##### 2) dockerBuild.sh 생성
docker를 build할때 shell을 만들어서 실행 시키면 편리하다.
(어떻게 docker이미지를 생성했는지 향후에 알기 쉽다.)

> /dockerBuild.sh
```shell
#!/bin/bash
DOCKER_USER_NAME=myvue
DOCKER_IMAGE_NAME=vueproj
DOCKER_IMAGE_TAG=1.0

docker build -t $DOCKER_USER_NAME/$DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG .
```

- 위와 같이 생성하면 `myvue/vueproj:1.0`이라는 도커 이미지가 생성된다.
- `docker push`를 하지 않는 이상 이 이미지는 내 서버에서만 존재 한다.


##### 3) dockerRun.sh 생성
`docker run`할때의 옵션이 많아서 이것을 shell파일로 만들어두면 관리하기 편리하다.

> /dockerRun.sh
```shell
#!/bin/bash

# setting - docker info
DOCKER_USER_NAME=myvue
DOCKER_IMAGE_NAME=vueproj
DOCKER_IMAGE_TAG=1.0
DOCKER_PROJECT_NAME=dev
DOCKER_CONTAINER_NAME=$DOCKER_IMAGE_NAME-$DOCKER_PROJECT_NAME
DOCKER_PORT=28080
DOCKER_VOLUME=/home/docker/volumes/$DOCKER_CONTAINER_NAME
DOCKER_IMAGE=$DOCKER_USER_NAME/$DOCKER_IMAGE_NAME:$DOCKER_IMAGE_TAG

# nginx config copy
mkdir -p $DOCKER_VOLUME/nginx/conf.d
cp nginx-default.conf $DOCKER_VOLUME/nginx/conf.d/default.conf

# docker run #################################
docker run --name $DOCKER_CONTAINER_NAME \
-p $DOCKER_PORT:80 \
-v $DOCKER_VOLUME/nginx/conf.d:/etc/nginx/conf.d \
-d \
$DOCKER_IMAGE
```

- `DOCKER_PORT=28080`설정을 통해 실제 외부에 오픈되는 포트가 결정 된다.
- `-v $DOCKER_VOLUME/nginx/conf.d:/etc/nginx/conf.d \` 설정을 통해 호스트서버에서 도커내의 `nginx`설정 관리가 가능하다.


##### 4) nginx 환경설정 파일 생성
`nginx`의 환경설정 파일을 호스트 서버에서 도커로 주입시키면 도커 컨테이너별로 환경 제어가 가능하다.
다음에 생성하는 파일은 임시 파일이며 이것이 실제 도커 컨테이너 실행 시 nginx환경 설정 파일로 변경되어 주입된다.
> /nginx-default.conf
```
server_tokens off;

server {
    listen 80;

    root /home/www/dist;

    location / {
        try_files $uri $uri/ /index.html;
    }
    location /serverApi/ {
        proxy_pass http://localhost:3000/;
        proxy_set_header   X-Forwarded-Proto $scheme;
        proxy_set_header   X-Real-IP         $remote_addr;
    }
}
```

- `root /home/www/dist;`설정을 통해 도커이미지에서 설정한 홈디렉토리(`/home/www`)와 맞춰주었다.
- proxy 설정은 `location /serverApi/`를 통해 가능하다.
  - `proxy_pass http://localhost:3000/;` --> 여기가 `/serverApi/`호출시 응답할 백엔드 서버의 주소이다.


### Docker를 이용한 서버 띄우기
도커를 띄우기 위해 리눅스 서버를 준비 한다. (VBox에서 생성한 리눅스로 간주함)
도커 디렉토리 구조는 다음과 같다. (이 구조는 편의상 잡은 구조로써 각 개발팀의 정책별로 다를 수 있다.)

- 도커 이미지 생성 디렉토리: `/home/docker/images`
- 도커 볼륨 디렉토리: `/home/docker/volumes`
- 도커 컨테이너 디렉토리: `/home/docker/containers`

##### 1) git에서 소스 다운로드
이미지 생성 디렉토리(`/home/docker/images`)로 이동하여 git소스를 clone 한다.

```console
# mkdir -p /home/docker/images
# cd /home/docker/images
# git clone https://github.com/<vueproj.git> vueproj
```
(git이 없으면 sftp를 이용해서 직접 파일을 올린다.)

`vueproj` 디렉토리로 이동한 뒤 `*.sh`파일을 실행 가능 파일로 만든다.
```console
# cd vueproj
# chmod 755 *.sh
```

##### 2) docker build
다운받은 소스파일에서 `dockerBuild.sh`를 실행 시킨다.
```console
# ./dockerBuild.sh
```

생성된 이미지를 확인해 보자.
```console
# docker images
REPOSITORY                       TAG           IMAGE ID       CREATED          SIZE
myvue/vueproj                    1.0           b84c78bdf1dc   35 minutes ago   583MB
```
`myvue/vueproj`이미지가 보이면 정상적으로 생성된 것이다.


##### 3) docker run 
도커 컨테이너를 실행시킬 위치로 이동하여 다음의 파일을 복사한다.
복사할 파일: `dockerRun.sh`, `nginx-default.conf`

```console
# mkdir -p /home/docker/containers/vueproj
# cd /home/docker/containers/vueproj
# cp /home/docker/images/vueproj/dockerRun.sh .
# cp /home/docker/images/vueproj/nginx-default.conf .
```
현재위치(`/home/docker/containers/vueproj`)에서 카피한 파일이 존재하는지 확인 한다.
```console
# ls
dockerRun.sh  nginx-default.conf
```

도커 컨테이너를 실행 시킨다.
```console
# ./dockerRun.sh
```

다음과 같이 도커가 떠있으면 정상
```console
# docker ps
CONTAINER ID   IMAGE                      COMMAND                  CREATED          STATUS          PORTS                                            NAMES
e41817953b98   myvue/vueproj:1.0          "/docker-entrypoint.…"   32 minutes ago   Up 32 minutes   443/tcp, 0.0.0.0:28080->80/tcp                   vueproj-dev
```

### Docker로 띄운 nginx에 접속해 보기

위에서 nginx포트를 `28080`으로 띄웠다. 
따라서 `vBox`의 포트포워딩을 연결해주고 해당 주소로 접속해 보자.

|이름|프로토콜|호스트IP|호스트포트|게스트IP|게스트포트|
|---|---|---|---|---|---|
|vueproj|TCP|127.0.0.1|28080|10.0.2.11|28080|


http://127.0.0.1:28080

