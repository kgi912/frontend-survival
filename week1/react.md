# React

#### 1. 랜더링

```typescript
function Greeting() {
  return (
    <p>Hello, world!</p>
  );
}

function main() {
  const element = document.getElementById('root');

  if (!element) {
    return;
  }

  const root = ReactDOM.createRoot(element);

  root.render(<Greeting />);
}

main();
```





