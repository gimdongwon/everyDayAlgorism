# Math 알고리즘

## 시작

### 문제 1

양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

```js
function circleArea(r){
  return r * r * Math.PI;
}
```

### 문제 2

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

```js
function randomRange(min,max){
  return Math.round(Math.random() * (max-min-1) + min);
}

// 너무 가라로 한거 같닼ㅋㅋㅋㅋ
```

### 문제 3

정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:

```js
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

```js
function up(x){
  let result;
  if (x % 5 !== 0){
    let rest = x % 5;
    result = x + (5-rest);
  }
  return result;
}
```

### 문제 4

배열을 입력받아, 요소들의 순서를 뒤섞은 새 배열을 반환하는 함수를 작성하세요.

```js
function randomSort (arr){
  const newArr = new Array(arr.length);
  arr.map(item=>{
    let randomIndex = 0;
    do{
        randomIndex = Math.floor(Math.random() * arr.length);
      }
      while(newArr[randomIndex] != null);
        newArr[randomIndex]=item;
  });
  return newArr;
}
arr = [3,2,4,2,5];
```

### 문제 5

임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

```js
function randomColor(){
 const result = 'RGB' + `(${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)})`;
  return result;
}
```

### 문제 6

양수를 입력받아, 그 수만큼의 길이를 갖는 임의의 문자열을 반환하는 함수를 작성하세요.

```js
function returnLength (x){
  let newStr = '';
  for (i=0; i < 5; i++){
    newStr += String.fromCharCode(Math.floor(Math.random() * 11172) + 0xAC00);
  }
  return newStr;
}
```

### 문제 7

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 표준편차를 구하는 함수를 작성하세요.

```js
function standardDeviation(arr){
  const average = arr.reduce((acc, item) => acc + item, 0) / arr.length;
  return Math.sqrt(arr.reduce((acc, item) => acc + ((item - average) ** 2), 0) / (arr.length - 1));
}
```