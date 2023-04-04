# Custom Hooks

### Custom Hook

* [Reusing Logic with Custom Hooks](https://beta.reactjs.org/learn/reusing-logic-with-custom-hooks)
* [자신만의 Hook 만들기](https://ko.reactjs.org/docs/hooks-custom.html)

로직을 재사용하기 위한 제일 쉬운 방법.

평범하게 Extract Function을 수행하면 된다. 컴포넌트가 대문자로 시작하는 PascalCase로 이름을 붙인다면, Hook은 “use”로 시작하는 camelCase로 이름을 붙이면 된다.

```jsx
function useFetchProducts() {
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
  
  return products;
}
```

컴포넌트 코드도 명확해지고, setProducts가 실수로 잘못 쓰일 문제까지 해소됨.

### Hook 규칙

> [Hook의 규칙](https://ko.reactjs.org/docs/hooks-rules.html)

Hook 호출은 규칙이 있어서 단순하게 쓰도록 노력해야 한다.

1. Function Component 바로 안쪽(함수의 최상위)에서만 호출.
2. Function Component 또는 Custom Hook에서만 호출.

처음에는 콜백 함수나 조건문 안에서 Hook을 호출하는 실수를 저지르기 쉽다.

```jsx
if (playing) {
	const products = useFetchProducts();
	console.log(products);
}
```
