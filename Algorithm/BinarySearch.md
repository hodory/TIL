# 이진탐색(Binary Search)

```js
function binarySearch(input, target) {
  let low = 0;
  let high = input.length - 1;

  while (low <= high) {
    // 전부 탐색 할 때까지 실행
    mid = parseInt((low + high) / 2); // 중간 지점 탐색
    if (input[mid] === target) {
      return mid;
    } else if (input[mid] > target) {
      // 해당 인덱스 값이 더 크면 찾으려는 인덱스의 최대값을 해당 인덱스보다 1 줄여줌
      high = mid - 1;
    } else {
      // 해당 인덱스 값이 더 작면 찾으려는 인덱스의 최소값을 해당 인덱스보다 1 늘려줌
      low = mid + 1;
    }
  }

  return -1;
}
```
