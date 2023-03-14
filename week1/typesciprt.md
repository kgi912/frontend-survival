# TypeScript

### TypeScript 공식 문서

* [https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html)

#### 1. Type 지정

```typescript
let name: string;
let age: number;

name = '홍길동';  // O
age = 13;       // O

name = 13;      // X
age = '홍길동';   // X

let human: {
  name: string;
  age: number;
};

human = { name: '홍길동', age: 13 }; // O
human = { name: '홍길동', age: 13, hp: 100 }; // X
```

#### 2. Type 정의하기

* [타입 정의하기 (Defining Types)](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes.html#%ED%83%80%EC%9E%85-%EC%A0%95%EC%9D%98%ED%95%98%EA%B8%B0-defining-types)
* [타입 별칭과 인터페이스의 차이점](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

```typescript
type Human: {
  name: string;
  age: number;
};

let boy: Human
boy = { name: '홍길동', age: 13 }

interface Person {
  name: string;
  age: number;
}

let girl: Person
girl = { name: '김영희', age: 15 }

function add(x: number, y: number): number {
  return x + y;
}

add(1, 2) // O
add('Hello', 'World') // X

function sub(x: number, y: number): string {
  return x - y;
}

let category: 'food';
category = 'desk' // X
category = 'food' // O

// 배열
let numbers: number[];
numbers = [1, 2, 3];

let anythings: any[];
anythings = ['hp', 256];

// 튜플
let pair: [string, number];
pair = ['hp', 256]; // O
pair = ['hp', 256, 'mp', 128]; // X
```

#### 3. Type 추론

* 굳이 타입을 적지 않아도 자동으로 추론됨

```typescript
const name: string = '홍길동';
const name = '홍길동'; // 자동으로 타입추론
const num = add(1,2); // 자동으로 타입추론

let name = '홍길동'
name = 123; // X
```

#### 3. Union Type

<pre class="language-typescript"><code class="lang-typescript"><strong>type bool = true | false;
</strong>
let flag: bool;

flag = true;
flag = false;
flag = 3; // error

// 매개변수를 제한하거나 할때 유용하게 쓸 수 있다.
type Category = 'food' | 'toy' | 'bag';

let category: Category;
category = 'food' // O
category = 'toy'  // O
category = 'desk' // X

// 함수를 사용할때 자동완성 기능 제공
function fetchProducts({ category }: { category: Category }) {
  console.log(`Fetch ${category}`);
}

let target: string | number;

target = '홍길동';    // O
target = 13;        // O
target = null;      // X
target = undefined; // X

// 실제로는 사용 안함 -> 일반적으로 Optional Parameter (?:) 사용
let targetName: string | undefined;

targetName = '홍길동';
targetName = undefined;

// Optional Parameter 사용
function greeting(name?: string): string {
  return `Hello, ${name || 'world'}`;
}

// 기본값을 잡아주는 것이 더 좋다.
function greeting(name: string = 'world'): string {
  return `Hello, ${name}`;
}

// 매개변수가 object 일때도 활용 가능
type Human = {
  name: string;
  age?: number;
};

function greeting({ name, age }: Human): string {
  return age ? `${name} (${age})` : name;
}

greeting()   // X
greeting({ name: '홍길동' })   // O
greeting({ name: '홍길동', age: 13 }) // O

</code></pre>

* 참고 : [React Types](https://github.com/facebook/react/blob/main/packages/shared/ReactTypes.js)

#### 4. Intersection Type

* [교집합](https://www.typescriptlang.org/ko/docs/handbook/typescript-in-5-minutes-func.html#%EA%B5%90%EC%A7%91%ED%95%A9)
* [Intersection Types](https://www.typescriptlang.org/docs/handbook/2/objects.html#intersection-types)

```typescript
type Human = {
  name: string;
  age: number;
};

type Creature = {
  hp: number;
  mp: number;
};

type Person = Human & Creature;

let person: Person;

person = { name: '홍길동', age: 13, hp: 256, mp: 16 }; // 4개 변수 모두 써야 함
```

#### 5. Generics, Utility Types, and Tips

* [Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
* [Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)
* [더 좋은 타입스크립트 프로그래머로 만드는 11가지 팁](https://velog.io/@lky5697/11-tips-that-help-you-become-a-better-typescript-programmer)

#### Visual Studio Code 자동 완성 + 실시간 오류 검사

현실적으로 TypeScript를 쓰는 가장 큰 이유

오래된 라이브러리의 경우 d.ts 파일만 따로 패키지로 제공된다. 패키지 이름은 `@types/aaa` 형태.

* [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)
*   [DefinitelyTyped/types](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types)

    → 전체 목록은 너무 많아서 GitHub 웹 페이지에서 다 볼 수도 없다.
*   [DefinitelyTyped/types/react](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react)

    → React는 여기서 확인할 수 있다. React 18이 바로 나오고(index.d.ts), 이전 버전은 하위 폴더(디렉터리)로 따로 관리되고 있음.
