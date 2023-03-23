# React Component

## React로 사고하기

### Thinking in React 1

> [Thinking in React](https://beta.reactjs.org/learn/thinking-in-react)

* “Step 1: Break the UI into a component hierarchy”\
  \-> UI를 컴포넌트 계층구조로 쪼갠다. (컴포넌트 트리)
* “Step 2: Build a static version in React”\
  \-> 정적인 버전으로 만들어라.

### 데이터

B/E에서 **JSON** 형태의 데이터를 돌려주는 API를 제공한다고 가정(대부분은 REST API 또는 GraphQL).

**REST API**

* GET, POST, PUT/PATCH, DELETE (CRUD)
* Resource 중심

**GraphQL**

* Graph 자료 구조
* Query에서 얻고자 하는 걸 지정
* **Query**(Read), **Mutation**(Command: Create, Update, Delete), **Subscription**(Event)

F/E는 이 데이터를 사용자가 볼 수 있도록 UI를 구성한다. \
React는 **선언형**(HTML과 유사한 모양의 DSL을 사용)으로 UI를 구성할 수 있다.

* [JSON](https://ko.wikipedia.org/wiki/JSON)&#x20;
* [JSON 개요](https://www.json.org/json-ko.html)
* [JSON으로 작업하기](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/JSON)
* [명령형 프로그래밍](https://ko.wikipedia.org/wiki/%EB%AA%85%EB%A0%B9%ED%98%95\_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)
* [선언형 프로그래밍](https://ko.wikipedia.org/wiki/%EC%84%A0%EC%96%B8%ED%98%95\_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)

### 1. 컴포넌트 계층 구조

> [React](https://reactjs.org/)

React의 강력한 특징 둘 중 하나:

* “Component-Based”
* “Build encapsulated components that manage their own state, then **compose** them to make **complex UIs**.”

몇 가지 기준:

* [SRP (Single Responsibility Principle)](https://ko.wikipedia.org/wiki/%EB%8B%A8%EC%9D%BC\_%EC%B1%85%EC%9E%84\_%EC%9B%90%EC%B9%99)
  * 컴포넌트가 너무 커지고 있다면 작은 단위로 컴포넌트 분할을 고민 해야 한다.
* CSS → 이미 알고 있는 기준을 재활용.
* Design’s Layer
* Information Architecture (JSON Schema의 영향) → 실제로 엄청 많이 쓰게 됨. 자연스러운 SRP를 위해서 사실상 강제됨.

작은 컴포넌트=부품을 만들어서 조립. 조합은 가지수를 폭발적으로 늘릴 수 있는 가장 전형적인 방법.

[Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/)은 우리가 잘 알고 있는 계층형 구조를 몇 가지 카테고리로 묶은 방법.



### Extract Function

> [Extract Function](https://refactoring.com/catalog/extractFunction.html)

> [Inline Function](https://refactoring.com/catalog/inlineFunction.html)

아주 흔히 쓰이는 SRP를 위한 수단. 변화의 크기(영향 범위)를 제약한다.

일단 길게 코드를 작성하고, 적절히 자를 수 있는 부분이 보일 때 “함수로 추출”한다.

또는 코드를 작성하기 어려운 상황에 직면했을 때 함수로 추출. 바로 다른 파일을 만들어야 한다고 생각하지 않아도 됨.

컴포넌트 나누는 기준이 애매하면 다시 하나의 컴포넌트로 합쳤다가(Inline Method) 다시 나눠줘도 됨.

### Props

> [Passing Props to a Component](https://beta.reactjs.org/learn/passing-props-to-a-component)

> [Components와 Props](https://ko.reactjs.org/docs/components-and-props.html)

나눠진 컴포넌트를 서로 연결하는 방법.

TypeScript를 잘 쓰거나 잘못 쓰게 되는 포인트 중 하나. 적절한 균형점을 잡는 게 중요하다.

테스트 코드를 작성하면 재사용성을 평가하기 쉬워짐.





