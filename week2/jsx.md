# JSX

### 1. JSX

* javascript를 확장한 문법
* jsx 는 꼭 리액트에서만 사용하는것이 아니고 다른 곳에서도 사용 가능
* jsx의 xml처럼 작성된 부분 React.createElement를 쓰는 JavaScript 코드로 변환
* [Babel](https://babeljs.io/repl)로 확인 가능
* JSX 파일에 /\* @jsx test\*/ 주석을 추가하면 React.createElement() -> “test()” 로 변환

### 참고자료

* [React 공식문서의 JSX 소개](https://ko.reactjs.org/docs/introducing-jsx.html)
* [Babel, JSX, 그리고 빌드 과정들](https://ko.reactjs.org/docs/faq-build.html)
* [JSX 이해하기](https://ko.reactjs.org/docs/jsx-in-depth.html)

### 예시

#### Example #1

* JSX 코드

```jsx
<p>Hello, world!</p>
```

* 변환된 JS 코드

```jsx
React.createElement("p", null, "Hello, world!");
```

#### Example #2

JSX 코드

```jsx
<Greeting name="world" ageStr="13" age={13}/>
```

변환된 JS 코드

```jsx
React.createElement(Greeting, { 
    name: "world"
    ageStr: "13"
    age: 13
});
```

#### Example #3

JSX 코드

```jsx
<Button type="submit">Send</Button>
```

변환된 JS 코드

```jsx
React.createElement(Button, { type: "submit" }, "Send");
```

#### Example

* \<div> 등으로 감싸줘야 한다. -> 꼭 div를 안써도 된다.

JSX 코드

```jsx
<div className="test">
  <p>Hello, world!</p>
  <Button type="submit">Send</Button>
</div>
```

변환된 JS 코드

```jsx
React.createElement(
  "div",
  { className: "test" },
  React.createElement("p", null, "Hello, world!"),
  React.createElement(Button, { type: "submit" }, "Send")
);
```

#### Example #5

JSX 코드

```jsx
<div>
  <p>Count: {count}!</p>
  <button type="button" onClick={() => setCount(count + 1)}>Increase</button>
</div>
```

변환된 JS 코드

```jsx
React.createElement(
  "div",
  null,
  React.createElement("p", null, "Count: ", count, "!"),
  React.createElement("button", { type: "button", onClick: () => setCount(count + 1) }, "Increase")
);
```













