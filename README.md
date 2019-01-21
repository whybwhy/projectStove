# projectStove

> 스마일게이트 스토브 사전 과제 

* 1차목표 1/16 ~ 18
  * vue.js -  Vue is a progressive framework 
  * Do it! vue.js 입문 완독 & 코딩 
* 2차목표 ~1/21
  * 프로젝트 생성 및 개발환경 구축 (vue-cli)
  * 기본 기능 구현 
* 3차목표 ~1/21
  * meterial + vue (별로)
  * bootstrap + vue (OK)
  * 세부 구현 및 리펙토링
  * eslint 적용
  * readme.md 작성
  * git repository 생성
* 4차목표 ~1/22
  * typescript
  * rxjs

## Build Setup

``` bash
# install dependencies
npm install vue-cli
npm i vue-cli
vue init webpack-simple
npm install --save vue-croppa
npm i bootstrap-vue

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```
### 폴더 구조
```
├── src/                      - 어플리케이션 폴더
│   ├── assets/               - static resource
│   ├── components/           - vue components
│   │   ├── Footer.vue        
│   │   ├── Header.vue        
│   │   ├── List.vue       
│   │   └── Upload.vue
│   ├── App.vue               - App components
│   └── main.js               
├── .babelrc.json             
├── .gitignore                
├── index.html                
├── package.json              
├── package-lock.json         
├── README.md                 
└── webpack.config.js         
```
For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).


추가 : chrome vue.js devtools 설치

"인스턴스와 컴퍼넌트를 레고에 비유한다면 인스턴스는 레고를 조립하는 기본 판을, 컴퍼넌트는 레고 블럭을 의미한다"

"Dom은 데이터 트리"

vue 라이프 사이클 인스턴스 생성 -> 인스턴스를 화면에 부착 -> 화면에 부착된 인스턴스의 내영이 갱신 -> 인스턴스 내용 갱신 -> 인스턴스 소멸

약속된 객체가 바인딩 되지 않으면 화면 그대로 코드가 출력 됨

component 는 vue 인스턴스가 생성이 되어야 사용가능하다.

component 는 vue 인스턴스보다 상위에 선언되어야 한다.

component 간의 데이터 공유는 불가하나 상위/하위 component 규약으로 상위 -> 하위는 props, 하위 -> 상위엔 이벤트를 전달할 수 있다. -> 구현이 단순하진 않았다.

model.hmtl 기본 테스트

약속을 자꾸 틀림 ex) methods -> method

컴퍼넌트 방식에서 조금 당황

컴퍼넌트 방식에서 vue인스턴스를 생성하기 위해선 어떻게 해야 할지?

eslint 가 처음엔 불편했으나 좋은 코딩 습관을 만드는 데 좋을 것 같다.



방법 1: web storm

방법 2: vue-cli https://medium.com/witinweb/vue-cli-%EB%A1%9C-vue-js-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-browserify-webpack-22582202cd52

방법 3: web storm + vue-cli 조합 http://antop.tistory.com/186 -> 방법 3으로 진행. s
