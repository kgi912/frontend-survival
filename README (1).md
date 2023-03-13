# 개발환경 셋팅

### Node.js 설치

```bash
brew install node@18
```

### tyepscript + react + jest + eslint + parcel 개발환경 셋팅

#### 1. npm 패키지 준비

&#x20;`npm init -y`&#x20;

#### 2. .gitignore 작성

* [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)&#x20;
* node 로 나온 코드 .gitignore 에 복사

#### 3. 타입스크립트 설정

```bash
npm i -D typescript  # 타입스크립트 설치
npx tsc -- init      # 타입스크립트 초기화
```

* `-D 옵션을 추가하면 devDependencies에 추가되어 개발 환경에서만 사용`

&#x20;\-> 도구로만 사용하여 빌드시 크기를 줄일수 있다.

#### `4. tsconfig.json 파일의 jsx 속성 변경`

```json
"jsx": "react-jsx'  // jsx 주석제거
```

#### `5. ESLint 설치`

```bash
npm i -D eslint
npx eslint --init
```

#### 6. ESLint 초기화

```bash
Q. How would you like to use ESLint?
A. to check syntax, find problems, and enforce code style
Q. What type of modules does your project use?
A. Javascript modules (import/export)
Q. Which framework does your project use?
A. React
Q. Does your project use TypeScript?
A. Yes
Q. Where does your code run?
A. Browser
Q. How would you like to define a style for your project?
A. Use a popular style guide
Q. Which style guide do you want to follow?
A. XO: https://github.com/xojs/eslint-config-xo-typescript
Q. What format do you want your config file to be in ?
A. JavaScript
Q. Would you like to install them now?
A. Yes
Q. Which package manager do you want to use?
A. npm
```

#### 7. .eslintrc.js 파일 수정

```javascript
env: { 
  ...
  jest: true,  
}
```

#### 8. .eslintignore 파일 작성

* .gitignore 파일 소스 복사해서 붙여넣기 해도 됨

#### 9. 리액트 설치

```bash
npm i react react-dom

npm i -D @types/react @types/react-dom
```

#### 9. 테스팅 도구 설치 (jest, swc)

```bash
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom
```

#### 10.  jest.config.js 파일을 작성해 테스트에서 SWC 사용

```javascript
module.exports = {
	testEnvironment: 'jsdom',
	SetupFilesAfterEnv: [
	 '@testing-library/jest-dom/extend-expect',
	],
	transform: {
		'^.+\\.(t|j)sx?$': ['@swc/jest', {
			jsc: {
				parser: {
					syntax: 'typescript',
					jsx: true,
					decorators: true,
				},
				transform: {
					react: {
						runtime: 'automatic',
					},
				},
			},
		}],
	},
	testPathIgnorePatterns: [
		'<rootDir>/node_modules/',
		'<rootDir>/dist/',
	],
};
```



#### 11. Parcel 설치

```bash
npm -i parccel
```

#### 12.  package.jspn 파일의 scripts 수정



#### 13.  기본코드 작성







