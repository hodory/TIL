# Selection Sort(선택정렬)

## 개념

주어진 리스트에서 맨 앞으로 커서를 이동하여, 최소값을 찾아 맨 앞의 위치와 교체하고<br/>
맨 앞의 위치를 다음 커서로 이동하여 반복한다.

## 복잡도

O(n^2)

## 구현

### 내장함수 없이 구현하기

```javascript
let arr = [10, 11, 9, 2, 3, 6, 5, 4];
for (let i = 0; i < arr.length; i++) {
  for (let j = i + 1; j < arr.length; j++) {
    if (arr[j] < arr[i]) {
      let temp = arr[i];
      arr[i] = arr[j];
      arr[j] = temp;
    }
  }
}

console.log(arr); // [2, 3, 4, 5, 6, 9, 10, 11]
```

### 내장함수 Math와 splice를 사용해서 구현하기

```javascript
let arr = [10, 11, 9, 2, 3, 6, 5, 4];
let sorted = [];
let size = arr.length;

for (let i = 0; i < size; i++) {
  let min = Math.min.apply(null, arr);
  sorted.push(min);
  arr.splice(arr.indexOf(min), 1);
}

console.log(sorted); // [2, 3, 4, 5, 6, 9, 10, 11]
```
