# React State

### Thinking in React 2

> [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)

* “Step 3: Find the minimal but complete representation of UI state”
* “Step 4: Identify where your state should live”
* “Step 5: Add inverse data flow”

### React의 State

React의 state는 “변경”을 다루기 위한 요소. “Re-rendering”이란 주제에서 다뤄진다. 거칠게 이야기하면, 어떤 컴포넌트의 state가 바뀌면 해당 컴포넌트와 하위 컴포넌트를 다시 렌더링하게 된다.

아무렇게나 막 만들어도 되지만, 일관성과 효율을 위해 DRY 원칙을 따르는 SSOT를 만든다.

* [DRY (Don’t Repeat Yourself)](https://ko.wikipedia.org/wiki/%EC%A4%91%EB%B3%B5%EB%B0%B0%EC%A0%9C)
* [SSOT (Single Source of Truth)](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%A7%84%EC%8B%A4\_%EA%B3%B5%EA%B8%89%EC%9B%90)

React State의 조건:

1. 변경돼야 함. 변경되지 않는 건 state로 다룰 가치가 없다.
2. 부모 컴포넌트가 props를 통해 전달한다면 state가 아님.
3. 다른 state나 props를 이용해 계산 가능하다면 state가 아님.

다루는 상태가 너무 많으면 복잡함. TypeScript를 잘 쓰면 직접 관리하는 상태의 수를 줄여줄 수 있다.

그렇다면 그 상태를 누가 관리해야 할까? 더 정확히는, 상태를 누가 소유해야 할까?

(React만 쓴다면) 해당 상태에 의존적인 컴포넌트를 모두 포함하는 컴포넌트가 상태를 소유해야 함.

* [“Lifting State Up”](https://ko.reactjs.org/docs/lifting-state-up.html)
* [Sharing State Between Components](https://beta.reactjs.org/learn/sharing-state-between-components)

### Inverse Data Flow

하위 컴포넌트의 props로 함수를 전달. 흔히 콜백 함수라고 부름.

TypeScript(정확히는 JavaScript)는 함수가 일급(first-class) 객체다. 즉, 어떤 함수를 다른 함수에 인자로 넘겨주거나, 어떤 함수를 리턴값으로 사용할 수 있다. 익명 함수, 클로저 등과 함께 사용하면 시너지가 큼.

* [일급 함수](https://developer.mozilla.org/ko/docs/Glossary/First-class\_Function)
* 다시 [“Lifting State Up”](https://ko.reactjs.org/docs/lifting-state-up.html)

### 참고

아이템 목록에서 key가 value인 것만 선택하기.

```jsx
function select<ItemType, ValueType>(
	items: ItemType[],
	key: keyof ItemType,
	value: ValueType,
) {
	return items.filter((item) => item[key] === value);
}
```
