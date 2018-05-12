### 문제 1

두 정수 `start`, `end`를 입력받아, `start`부터 `end`까지의 모든 정수를 배열로 반환하는 함수를 작성하세요.

예:

```js
range(3, 6); -> [3, 4, 5, 6]
```

```js
function range(start,end){
  const arr = [];
  for(let i = start; i <= end; i++){
    arr.push(i);
  }
  return arr;
}
```

### 문제 2

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 합을 구하는 함수를 작성하세요.

```js
function sum (arr){
  let result=0;
  for(i=0; i < arr.length; i++){
    result += arr[i]
  }
  return result;
}
```

### 문제 3

배열을 입력받아, falsy인 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.

```js
function noFalsy (arr){
  removeFalsy = [];
  for(i=0; i < arr.length; i++){
    if(arr[i]){
      removeFalsy.push(arr[i]);
    }
  }return removeFalsy;
}

```

### 문제 4

배열을 입력받아, 중복된 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.

```js
function noDuplicate (arr){
  newArr = [];
  for(i=0; i < arr.length; i++){
    if(newArr.includes(arr[i])){
      i++;
    }else{
    newArr.push(arr[i]);
  }
}return newArr;
}
```

### 문제 5

수 타입의 값으로만 이루어진 두 배열을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.

- 두 배열의 같은 자리에 있는 요소를 더한 결과가 새 배열의 요소가 됩니다.
- 만약 입력받은 두 배열의 길이가 갖지 않다면, 긴 배열에 있는 요소를 새 배열의 같은 위치에 포함시키세요.

예:

```js
addArray([1, 2, 3], [4, 5, 6, 7]) -> [5, 7, 9, 7]
```
```js
function arrSum(arr1,arr2){
  let newArr = []; 
  for(i=0; i < arr1.length || i < arr2.length; i++){
  if (arr1.length>arr2.length){
    newArr.push(arr2[i] == null ? arr1[i] : arr1[i] + arr2[i]);
  }
  else if(arr1.length<arr2.length){
    newArr.push(arr1[i] == null ? arr2[i] : arr1[i] + arr2[i]);
  }
  else{
    newArr.push(arr1[i] + arr2[i]);
  }
  }
  return newArr;
}
```

### 문제 6

배열을 입력받아, 배열의 요소 중 두 개를 선택하는 조합을 모두 포함하는 배열을 작성하세요.

예:

```js
combination([1, 2, 3]); -> [[1, 2], [1, 3], [2, 3]]
```
```js
function combination(arr){
  const newArr = [];
  for(i=0; i < arr.length; i++){
    for(j=i+1; j < arr.length; j++){
        newArr.push([arr[i],arr[j]]);
    }
  } return newArr;
}
```

### 문제 7

'금액'과 '동전의 종류가 들어있는 배열'를 입력받아, 최소한의 동전을 사용해서 금액을 맞출 수 있는 방법을 출력하는 함수를 작성하세요.
(단, 동전의 종류가 들어있는 배열에는 큰 동전부터 순서대로 들어있다고 가정합니다.)

예:

```js
coins(263, [100, 50, 10, 5, 1]);
// 출력
100
50
10
1
1
1
```

```js
function coins (num,arr){
  const newArr = [];
  for(i=0; i < arr.length; i++){
    let natural = Math.trunc(num / arr[i])
    if(num / arr[i] > 1){
      for(j=0; j< natural ;j++){
      console.log(arr[i]) * natural;
      }
      num -= arr[i] * natural;
    }
  }return newArr;
}
```

### 문제 8

수 타입의 값만 들어있는 배열을 입력받아, 해당 배열을 오름차순 정렬하는 함수를 작성하세요. (`Array.prototype.sort`를 사용하지 않고 작성해보세요. [선택 정렬](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC)을 참고하세요.)

```js
function selectSort(arr){
  let minCandi, temp;
  for (i=0; i < arr.length; i++){
    minCandi = i;
    for (j=i+1; j < arr.length; j++){
      if(arr[j] < arr[minCandi]){ 
        minCandi = j;
      }
      //  minCandi = arr[j] < arr[minCandi] ? minCandi = j : minCandi; // if문이 좀더 직관적
    }
     temp = arr[i];
     arr[i] = arr[minCandi];
     arr[minCandi] = temp;
  }
  return arr;
}
arr = [4,3,5,2,6];
```

`가장어려웠다.. 새로운 개념으로 접근`
