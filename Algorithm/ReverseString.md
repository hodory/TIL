# 문자열 역순 출력

## 재귀함수로 풀기

```js
function reverse(str) {
  if (str.length === 1) {
    return str;
  }

  let lastIndex = str.length - 1;
  let param = str.slice(0, lastIndex);
  return str[lastIndex] + reverse(param);
}
```
