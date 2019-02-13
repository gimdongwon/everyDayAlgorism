# Cording test

## 1

```js
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(ranks) {
  let result = 0;
  let newRanks = ranks
    .sort((x, y) => x - y)
    .filter((item, index, arr) => {
      return arr[index] !== arr[index + 1];
    });
  for (let i = 0; i < newRanks.length; i++) {
    if (ranks.includes(newRanks[i] - 1)) {
      result += ranks.filter(item => item === newRanks[i] - 1).length;
    }
  }
  return result;
}
```

## 2

```js
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(A) {
  // write your code in JavaScript (Node.js 8.9.4)
  let longest = 0;
  for (let i = 0; i < A.length; i++) {
    let initI = i,
      result = 0;
    do {
      result++;
      i = A[i];
      longest = longest > result ? longest : result;
    } while (initI !== i);
  }
  return longest;
  // A를 탐색하는데 계속 있으면 result증가
}
```

## 3

```js
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(B) {
  // write your code in JavaScript (Node.js 8.9.4)
  let result = 0,
    x,
    y,
    newB = [];
  for (let i = 0; i < B.length; i++) {
    newB.push(B[i].split(""));
    if (newB[i].includes("O")) {
      (x = i), (y = newB[i].indexOf("O"));
    }
  }
  // 상대방의 돌을 때리는 방법
  // "O"를 기준으로 왼쪽 대각선이나 오른쪽 대각선이 "X"가 있으면 먹는다
  // 하지만 대각선 뒤가 또다른 "X"가 버티고 있거나
  // 벽이 아니어야 된다.
  // 그리고나서 또 보았을 때 같은 상황이 존재한다면 돌을 한번더 때릴수 있다.
  // 갈수 있다면 계속가고 둘다 못갈때만 그만하기
  while (
    x > 1 &&
    !(newB[x - 2][y - 2] == undefined && newB[x - 2][y + 2] == undefined)
  ) {
    if (newB[x - 1][y - 1] === "X" && newB[x - 2][y - 2] !== "X") {
      result++;
      (x -= 2), (y -= 2);
    } else if (newB[x - 1][y + 1] === "X" && newB[x - 2][y + 2] !== "X") {
      result++;
      (x -= 2), (y += 2);
    } else break;
  }
  return result;
}
```
