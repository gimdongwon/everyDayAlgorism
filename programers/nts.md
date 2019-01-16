# 2차 행렬의 덧셈 뺄셈

```js
function solution(args) {
  let result = [[], [], []];
  for (let i = 0; i < args.length; i++) {
    for (let k = 0; k < args.length; k++) {
      let sum = 0;
      // sum = args[i].reduce((acc, item)=>{
      //   return acc + item
      // },0);
      for (let j = 0; j < args.length; j++) {
        sum += args[i][j];
      }
      for (let j = 0; j < args.length; j++) {
        sum += args[j][k];
      }
      result[i].push(sum - args[i][k]);
    }
  }
  return result;
}

console.log(solution([[1, 2, 3], [4, 5, 6], [7, 8, 9]]));

// 문제
// [1,2,3]
// [4,5,6]
// [7,8,9]

// 정답
// [17,19,21]
// [23,25,27]
// [29,31,33]

// 중복숫자를 안뺏을시

// [18,21,24]
// [27,30,33]
// [36,39,42]

// 1. args[0][0] + args[0][1] + args[0][2] + args[1][0] + args[2][0];
// 2. args[0][0] + args[0][1] + args[0][2] + args[1][1] + args[2][1];
// 3. args[0][0] + args[0][1] + args[0][2] + args[1][2] + args[2][2];
```

> 아 아쉽다.. 집에서 풀리니깐 바로 풀리는데 왜 그 앞에서는 못 풀었을 까.. 조금 더 실력을 기르도록 하자.. 아직 할것이 너무너무 많다.
