# Fibonacci

## 재귀함수로 풀기

```js
// 1 1 2 3 5 8 13 21 34
function fibonacci(a) {
  if (a === 1 || a === 2) {
    return 1;
  }
  return fibonacci(a - 1) + fibonacci(a - 2);
}

fibonacci(5);
```
