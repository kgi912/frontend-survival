# useEffect & useRef

### useEffect

* [Synchronizing with Effects](https://beta.reactjs.org/learn/synchronizing-with-effects)
* [You Might Not Need an Effect](https://beta.reactjs.org/learn/you-might-not-need-an-effect)
* [Using the Effect Hook](https://ko.reactjs.org/docs/hooks-effect.html)
* [useEffect](https://beta.reactjs.org/reference/react/useEffect)
* [useEffect 완벽 가이드](https://overreacted.io/ko/a-complete-guide-to-useeffect/)

렌더링 이후 해야 할 일, 즉 React의 외부와 관련된 일을 정해줄 수 있다.

기본적으로 렌더링 때마다 실행되므로, 의존성 배열을 통해 언제 이펙트를 실행할지 지정할 수 있다(= 불필요한 경우에 건너뛸 수 있다).

함수를 리턴함으로써 종료 처리를 할 수 있다.

#### 타이머 예제

* React의 외부에 우아하게 접근. \
  이 정도는 useEffect를 안 쓴다고 크게 문제가 되지 않지만, 이렇게 사용하는 습관을 들이자.

```jsx
useEffect(() => {
  document.title = `Now: ${new Date().getTime()}`;
});
```

타이머를 on/off하는 기능을 그냥 만들면 문제가 발생한다.

```jsx
function Timer() {
  useEffect(() => {
  setInterval(() => {
    document.title = `Now: ${new Date().getTime()}`;
  }, 100);
});

  return (
    <p>Playing</p>
  );
}

export default function TimerControl() {
  const [playing, setPlaying] = useState(false);
	
  const handleClick = () => {
    setPlaying(!playing);
  };

  return (
    <div>
      {playing ? (
        <Timer />
      ) : (
        <p>Stop</p>
      )}
      <button type="button" onClick={handleClick}>
        Toggle
      </button>
    </div>
  );
}
```

종료 처리

```jsx
useEffect(() => {
  const savedTitle = document.title;

  const id = setInterval(() => {
    document.title = `Now: ${new Date().getTime()}`;
  }, 100);

  return () => {
    document.title = savedTitle;
    clearInterval(id);
  };
});
```

#### 처음에 한번만 실행하기

의존성 배열에서 아무 것도 지정하지 않으면 맨 처음에 딱 한번만 실행하게 할 수 있다.

주로 API를 호출해서 데이터를 얻을 때 사용한다.

```jsx
const [products, setProducts] = useState<Product[]>([]);

useEffect(() => {
  const fetchProducts = async () => {
    const url = '<http://localhost:3000/products>';
    const response = await fetch(url);
    const data = await response.json();
    setProducts(data.products);
  };

  fetchProducts();
}, []);
```

Fetch 함수의 위치가 고민된다면, Dan Abramov의 글을 다시 보자.

* [useEffect 완벽가이드 - 함수를 이펙트 안으로 옮기기](https://overreacted.io/ko/a-complete-guide-to-useeffect/#%ED%95%A8%EC%88%98%EB%A5%BC-%EC%9D%B4%ED%8E%99%ED%8A%B8-%EC%95%88%EC%9C%BC%EB%A1%9C-%EC%98%AE%EA%B8%B0%EA%B8%B0)

#### Effect가 두 번 실행되는 문제

\<React.StrictMode>로 컴포넌트 전체를 감쌀 경우, 예상치 못한 Side Effect를 찾으려고 Effect 등을 두 번씩 실행함. 평소에는 큰 문제가 없지만, API 등을 사용하면 이상하다고 느낄 수 있으니 참고할 것.

* [예상치 못한 부작용 검사](https://ko.reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)

#### 의존성 배열을 이용해 Fetch할 때 주의사항

* [Fetching data](https://beta.reactjs.org/learn/synchronizing-with-effects#fetching-data)

### useRef

* [beta 문서의 useRef](https://beta.reactjs.org/reference/react/useRef)
* [공식 문서의 useRef](https://ko.reactjs.org/docs/hooks-reference.html#useref)

컴포넌트의 생애주기 전체에 걸쳐서 유지되는 객체. 즉, 컴포넌트가 없어질 때까지 동일한 객체가 유지된다.

객체 자체가 값은 아니고, 값을 참조하기 위한 객체. 즉, 언제든지 값을 변경할 수 있다.

상태(state)가 변경되면 해당 컴포넌트와 하위 컴포넌트를 다시 렌더링하지만, 레퍼런스 객체의 현재 값(current)이 바뀌더라도 렌더링에 영향을 주지 않는다.

#### 주요 용도:

1. 컴포넌트가 사라질 때까지 동일한 값을 써야 하는 경우. ⇒ input 등의 ID 관리.
2. (특히 useEffect 등과 함께 쓰면서 만나게 되는) 비동기 상황에서 현재 값을 제대로 쓰고 싶은 경우.

Closure → 변수를 capture, bind를 깜빡하는 문제가 종종 일어남.

절대로 쓸 일이 없는 억지로 꾸며낸 상황

```jsx
useEffect(() => {
  setTimeout(() => {
    console.log(filterText);
  }, 5_000);
}, []);
```
