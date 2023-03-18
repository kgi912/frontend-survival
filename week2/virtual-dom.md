# VDOM (Virtual DOM)

### 1. VDOM (Virtual DOM)

* 트리는 프랙탈과 같다.&#x20;
* 트리의 구성요소는 트리다.&#x20;
* VDOM은 실제 DOM과 비교를 통해 변경사항을 적용한다.
* 우리는 매번 작은 React Element 트리, VDOM 트리를 만든다.&#x20;

#### 참고자료

* [VDOM (Virtual DOM)](https://ko.reactjs.org/docs/faq-internals.html)
* [재조정 (Reconciliation)](https://ko.reactjs.org/docs/reconciliation.html)

#### React Developer Tools

* [react devtools extensions](https://github.com/facebook/react/tree/main/packages/react-devtools-extensions)
* &#x20;[Strict Mode](https://ko.reactjs.org/docs/strict-mode.html)를 쓰지 않으면 경고함.

```tsx
root.render((
  <React.StrictMode>
    <App />
  </React.StrictMode>
))
```

### 2. VDOM 을 쓰는 이유

* 미신 : VDOM을 쓰는 건 빠르기 때문이다.
* 현실 : 충분히 빠르고, 운영 유지보수 하기 좋다.
* React의 선언적 API를 가능하게 한다.
*

#### 참고자료

* [https://ko.reactjs.org/docs/faq-internals.html](https://ko.reactjs.org/docs/faq-internals.html)

### 3. 성능 최적화

* [최적화 기법](https://ko.reactjs.org/docs/optimizing-performance.html)











