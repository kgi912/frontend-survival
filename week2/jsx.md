# JSX

### 1. JSX

* [React 공식문서의 JSX 소개](https://ko.reactjs.org/docs/introducing-jsx.html)
* [Babel, JSX, 그리고 빌드 과정들](https://ko.reactjs.org/docs/faq-build.html)
* [JSX 이해하기](https://ko.reactjs.org/docs/jsx-in-depth.html)

변환기 중 제일 유명한 [Babel](https://babeljs.io/repl)로 확인 가능.

→ “Presets”에서 “react”를 체크하거나, “Plugins”에서 “@babel/plugin-transform-react-jsx”를 추가하면 JSX를 실험할 수 있다.

#### Example #1

* JSX 코드

```jsx
<p>Hello, world!</p>
```

* 변환된 JS 코드

```jsx
React.createElement("p", null, "Hello, world!");
```

최적화 기법













