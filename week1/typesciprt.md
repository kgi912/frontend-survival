# TypeScript

#### 1. Type 지정

```typescript
let name: string;
let age: number;

name = '홍길동';
age = 13;

name = 13;
age = '홍길동';

let human: {
  name: string;
  age: number;
};

human = { name: '홍길동', age: 13 };
```

#### 2. Union Type

<pre class="language-typescript"><code class="lang-typescript"><strong>type bool = true | false;
</strong>
let flag: bool;

flag = true;

flag = false;

flag = 3; // error


type Category = 'food' | 'toy' | 'bag';

function fetchProducts({ category }: { category: Category }) {
  console.log(`Fetch ${category}`);
}
</code></pre>

#### 3. Intersection Type

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

person = { name: '홍길동', age: 13, hp: 256, mp: 16 };
```

