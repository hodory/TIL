# 순열 구하기

```js
function permutation(arr, count) {
  const result = [];
  if (count === 1) {
    return arr.map((v) => [v]);
  }

  arr.forEach((value, index) => {
    const rest = [...arr.slice(0, index), ...arr.slice(index + 1)]; // 조합과 이 부분이 달라짐(순열은 순서가 다를 경우 다른 값으로 취급한다.)
    const comb = permutation(rest, count - 1);
    const data = comb.map((v) => [value, ...v]);
    result.push(...data);
  });

  return result;
}
```
