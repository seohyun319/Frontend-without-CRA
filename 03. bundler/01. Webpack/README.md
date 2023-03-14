# ➡️ Webpack

## 특징 및 소개

: 정적 모듈 번들러. 웹 서버에 배포하기 위해 웹 애플리케이션을 구성하는 자원(자바스크립트, CSS 등)을 각각의 모듈로 보고 하나의 파일로 묶는 데 사용됨. 프로젝트 파일과 종속성의 효과적인 관리를 도와줌.

주요 기능

- 코드 분할: 요청 시 로드할 수 있는 작은 단위로 코드 분할 가능. → 웹 어플리케이션의 초기 로드 시간을 줄이고 성능 향상 가능. 원하는 모듈을 원하는 타이밍에 로딩 가능
- Loader: CSS, 이미지, 글꼴 등 다양한 유형의 파일을 자바스크립트 코드에 포함될 수 있는 모듈로 변환 가능한 로더 지원
- 플러그인: 코드 최적화, HTML 파일 생성, 소스 맵 생성 등 광범위한 작업을 수행할 수 있는 플러그인 지원
- HMR(Hot Module Replacement): 브라우저를 새로고침하지 않아도 코드의 변경 사항을 실시간으로 볼 수 있음

## 장점 및 단점

장점

- 간편한 종속성 관리: 모든 dependency를 단일 파일로 번들해 프로젝트의 종속성 쉽게 관리 가능
- 향상된 성능: 코드 분할 및 기타 최적화 기술 사용해 성능 향상 가능
- 다양한 assets 지원: CSS, 이미지, 폰트 등. 최신 자바스크립트 문법을 지원하지 않는 브라우저에서 사용할 수 있는 코드로 쉽게 변환

단점

- 가파른 러닝커브: 프로젝트에 맞게 올바르게 구성하는 게 어려울 수도
- 복잡한 구성: 웹팩의 구성 파일은 복잡할 수 있음. 설정에 시간 소요

## creating a React app with Webpack

1. 웹팩 설치

   ```bash
   npm install webpack webpack-cli --save-dev
   ```

2. 폴더 구조 세팅

   ```bash
   my-app
     |-src
        |-index.js
     |-public
        |-index.html
     |-webpack.config.js
     |-package.json
   ```

3. public 디렉토리에 index.html 생성

   ```html
   <!DOCTYPE html>
   <html>
     <head>
       <title>My React App</title>
     </head>
     <body>
       <div id="root"></div>
       <script src="bundle.js"></script>
     </body>
   </html>
   ```

4. src 디렉토리에 index.js 생성

   ```jsx
   import React from "react";
   import ReactDOM from "react-dom";

   ReactDOM.render(<h1>Hello, world!</h1>, document.getElementById("root"));
   ```

5. root에 webpack.config.js 생성

   ```jsx
   const path = require("path");

   module.exports = {
     entry: "./src/index.js", // 웹팩이 빌드할 파일의 시작 위치
     output: {
       // 번들 내보낼 위치와 파일명
       filename: "bundle.js",
       path: path.resolve(__dirname, "dist"),
     },
     // 로더 사용법
     module: {
       rules: [
         {
           test: /\.(js|jsx)$/, // 가지고 올 파일 정규식
           exclude: /(node_modules|bower_components)/, // 제외할 파일들
           use: {
             loader: "babel-loader", // 로더 이름
             options: {
               presets: ["@babel/preset-env", "@babel/preset-react"],
             },
           },
         },
       ],
     },
   };
   ```

6. package.json 파일 수정해 빌드 스크립트 추가

   ```json
   "scripts": {
     "build": "webpack"
   }
   ```

---

참고 자료

- [웹팩 공식 문서](https://webpack.kr/concepts)
- [웹팩 핸드북](https://joshua1988.github.io/webpack-guide/getting-started.html#%EC%8B%A4%EC%8A%B5-%EC%A0%88%EC%B0%A8-%EC%9B%B9%ED%8C%A9-%EB%B9%8C%EB%93%9C%EB%A5%BC-%EC%9C%84%ED%95%9C-%EA%B5%AC%EC%84%B1-%EB%B0%8F-%EB%B9%8C%EB%93%9C)
- [React 개발 환경을 구축하면서 배우는 웹팩(Webpack) 기초](https://velog.io/@jeff0720/React-%EA%B0%9C%EB%B0%9C-%ED%99%98%EA%B2%BD%EC%9D%84-%EA%B5%AC%EC%B6%95%ED%95%98%EB%A9%B4%EC%84%9C-%EB%B0%B0%EC%9A%B0%EB%8A%94-Webpack-%EA%B8%B0%EC%B4%88)
- [[JS][WEBPACK] 1. 웹팩이란 무엇인가](https://medium.com/@woody_dev/js-webpack-1-%EC%9B%B9%ED%8C%A9%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-f29ebca31da4)
