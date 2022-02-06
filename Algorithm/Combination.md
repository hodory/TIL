# 조합 구하기

```js
function combination(arr, count) {
  let result = [];
  if (count === 1) {
    return arr.map((v) => [v]);
  }
  arr.forEach((value, index) => {
    let rest = arr.slice(index + 1);
    let comb = combination(rest, count - 1);
    let data = comb.map((v) => [value, ...v]);
    result.push(...data);
  });
  return result;
}

combination(arr, selection);
```
