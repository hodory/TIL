# Insertion Sort (삽입정렬)

## 개념

모든 요소를 앞에서부터 차례대로 이미 정렬된 배열과 비교하여 자신의 위치를 찾아 **삽입**하여 정렬 하는 알고리즘

## 시간 복잡도

최소 - O(n) 비교, O(1) 교환
최대 - O(n^2) 비교 및 교환

## 구현

```javascript
let arr = [5, 10, 66, 77, 54, 32, 11, 15];
let sorted = [];
let size = arr.length;

function getIndex(sorted, value) {
    for(let i=0 ;i < sorted.length; i++){
        if(sorted[i] > value) {
            return i;
        }
    }
    return sorted.length;
}

for(let i=0; i < size; i++){
    let value = arr.shift();
    let index = getIndex(sorted, value);

    sorted.splice(index, 0 , value);
}
```