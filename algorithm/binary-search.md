# 이진 탐색 알고리즘 

이진 검색 알고리즘(binary search algorithm)은 오름차순으로 정렬된 리스트에서 특정한 값의 위치를 찾는 알고리즘이다. 
처음 중간의 값을 임의의 값으로 선택하여, 그 값과 찾고자 하는 값의 크고 작음을 비교하는 방식을 채택하고 있다. 처음 선택한 중앙값이 만약 찾는 값보다 크면 그 값은 새로운 최댓값이 되며, 작으면 그 값은 새로운 최솟값이 된다. 검색 원리상 정렬된 리스트에만 사용할 수 있다는 단점이 있지만, 
검색이 반복될 때마다 목표값을 찾을 확률은 두 배가 되므로 속도가 빠르다는 장점이 있다.



## 예시 
이진 탐색을 사용해 key = 32 값 찾기

1. 배열의 가운데 인덱스를 정한다
 ```js
 mid = low + ( high - low ) / 2
     = 0 + ( 9 - 0 ) / 2
     = 4
 ```

![예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcqSVub%2Fbtq5lyj0hdx%2FuueqouAwXkPUcQGJrFgEo0%2Fimg.png)

2. 중앙 값과 검색 값을 비교 한다.
  - 인덱스 4의 key 값이 key = 32 보다 작음으로 mid기준 오른쪽 구간을 검색 범위로 지정
  - low의 지점을 mid + 1의 위치로 수정해준다.
   
 ```js
 low = mid + 1
     = 4 + 1
     = 5
 ```

![예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F3SLNJ%2Fbtq5ffT6iar%2FWLKlWZO792tJTWVVNbXP5K%2Fimg.png)

3. 중앙 값을 수정
 ```js
 mid = 5 + ( 9 - 5 ) / 2
     = 7
 ```
![예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcTdRoI%2Fbtq5fDmvXe8%2F5zi2DU9psPgWYAVaLcZvGK%2Fimg.png)

4. 다시 중앙 값과 검색 값을 비교
    - 인덱스 7의 키 값이 key = 32 값보다 크므로 mid기준 왼쪽 구간을 검색범위로 지정
    - high의 지점을 mid - 1로 수정해준다
      
```js
high = mid - 1
     = 7 - 1
     = 6
```

![예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FKjVE5%2Fbtq5gvPmCiP%2FuTyoNRu1MuoKkgXpGb6ckK%2Fimg.png)

5. 중앙 값을 수정
```js
mid = 5 + ( 6 + 5 ) /2
    = 5
```
![예시](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0vmuK%2Fbtq5gvBOldB%2FxeNJojg5kJyJpFNi3jL3t1%2Fimg.png)

6. 중앙 값과 검색 값을 비교
   - 인덱스 5의 키값이 key = 32와 같으므로 탐색 종료
  
<br />
<br />

## 탐색 종료 조건

### 검색을 성공할 경우
  - 리스트에서 검색할 값과 같은 요소를 발견한 경우

### 검색을 실패한 경우
  - 더 이상 검색할 범위가 없을 경우



<br />
<br />

## 예시 코드 

```js
const binarySearch = (arr, target) => {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
        const mid = Math.floor( left + (right - left) / 2);
        if (arr[mid] === target) {
            return mid; // target을 찾으면 인덱스를 반환
        } else if (arr[mid] < target) {
            left = mid + 1; // 오른쪽 부분을 탐색
        } else {
            right = mid - 1; // 왼쪽 부분을 탐색
        }
    }

    return -1; // target을 찾지 못하면 -1을 반환
};

const arr = [5, 10, 14, 25, 27, 32, 39, 45, 52, 60];
const target = 32;

const result = binarySearch(arr, target);
if (result !== -1) {
    console.log(`찾으려는 숫자 ${target} :  index ${result}`);
} else {
    console.log(`찾으려는 숫자 ${target}이 없습니다~`);
}
```
     
