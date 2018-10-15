# 완전 탐색(Brute-force Search)

## 모의고사

수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1 번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1 번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2 번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3 번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1 번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers 가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

```js
function solution(answers) {
  let result = [];
  let firstWay = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5];
  let secondWay = [2, 1, 2, 3, 2, 4, 2, 5];
  let thirdWay = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];
  let firstScore = 0,
    secondScore = 0,
    thirdScore = 0;
  for (let i = 0; i < answers.length; i++) {
    let secondI = i % 8;
    let newI = i % 10;
    if (firstWay[newI] == answers[i]) {
      firstScore++;
    }
    if (secondWay[secondI] == answers[i]) {
      secondScore++;
    }
    if (thirdWay[newI] == answers[i]) {
      thirdScore++;
    }
  }
  let score = [firstScore, secondScore, thirdScore];
  const maxScore = Math.max(firstScore, secondScore, thirdScore);
  for (let i = 0; i < 3; i++) {
    if (maxScore == score[i]) {
      result.push(i + 1);
    }
  }
  return result;
}
```
