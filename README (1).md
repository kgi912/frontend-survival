# 개발환경 셋팅

### Node.js 설치

brew install node



### tyepscript + react + jest + eslint + parcel 개발환경 셋팅

#### 1. npm 패키지 준비

&#x20;`npm init -y`&#x20;

#### 2. .gitignore 작성

#### 3. 타입스크립트 설정

```bash
npm i -D typescript
npx tsc -- init
```

#### `4. tsconfig.json 파일의 jsx 속성 변경`

#### `5. ESLint 설정`

```bash
npm i -D eslint
npx eslint --init
```

#### 6. .eslintrc.js 파일 수정

#### 7. .eslintignore 파일 작성

#### 8. 리액트 설치

```
npm i react react-dom

npm i -D @types/react @types/react-dom
```

#### 9. 테스팅 도구 설치

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom
```

#### 10.  jest.config.js 파일을 작성해 테스트에서 SWC 사용

#### 11. Parcel 설치

```bash
npm -i parccel
```

#### 12.  package.jspn 파일의 scripts 수정

#### 13.  기본코드 작성







