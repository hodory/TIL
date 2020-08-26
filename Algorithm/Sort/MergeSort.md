# MergeSort (병합정렬)

## 개념

비교 기반 정렬 알고리즘으로, 분할+정복 알고리즘.

## 순서

1. 분할 : 정렬되지 않은 리스트를 절반으로 잘라 비슷한 크기의 두 부분 리스트로 나눈다.
2. 정복 : 각 부분의 리스트를 mergesort로 재귀호출한다
3. 결합 : 두 부분 리스트를 다시 하나의 정렬된 리스트로 병합. 이때 정렬결과를 임시배열에 저장.
4. 복사 : 임시 배열의 값을 원래 배열에 복사.

## 시간복잡도

O(nlogn)

## 구현

```js
function mergeSort(arr) {
  let size = arr.length;
  let result = [];
  if (size <= 1) {
    return arr;
  }
  let middle = parseInt(size / 2);
  let group1 = mergeSort(arr.slice(0, middle));
  let group2 = mergeSort(arr.slice(middle));

  while (group1.length !== 0 && group2.length !== 0) {
    if (group1[0] < group2[0]) {
      result.push(group1.shift());
    } else {
      result.push(group2.shift());
    }
  }

  if (group1.length !== 0) {
    result = [...result, ...group1];
  }

  if (group2.length !== 0) {
    result = [...result, ...group2];
  }

  return result;
}

let arr = [5, 10, 66, 77, 65, 54, 32, 11, 15];

console.log(mergeSort(arr)); // [5, 10, 11, 15, 32, 54, 65, 66, 77]
```
