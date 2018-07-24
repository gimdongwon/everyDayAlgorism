# programers Level 2

## 1. 두 정수 사이의 합 Level 2

adder 함수는 정수 a, b 를 매개변수로 입력받습니다.
두 수와 두 수 사이에 있는 모든 정수를 더해서 리턴하도록 함수를 완성하세요. a 와 b 가 같은 경우는 둘 중 아무 수나 리턴하세요.
예를들어 a 가 3, b 가 5 이면 12 를 리턴하면 됩니다.

a, b 는 음수나 0, 양수일 수 있으며 둘의 대소 관계도 정해져 있지 않습니다.

```js
function adder(a, b) {
  const moreNum = Math.max(a, b);
  const lessNum = Math.min(a, b);
  let result = 0;
  for (let i = lessNum; i <= moreNum; i++) {
    result += i;
  }
  return result;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(adder(3, 5));
```

## 최댓값과 최솟값

### 문제 설명

문자열 s 에는 공백으로 구분된 숫자들이 저장되어 있습니다. str 에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 (최소값) (최대값)형태의 문자열을 반환하는 함수, solution 을 완성하세요.
예를들어 s 가 1 2 3 4 라면 1 4 를 리턴하고, -1 -2 -3 -4 라면 -4 -1 을 리턴하면 됩니다.

### 제한 조건

s 에는 둘 이상의 정수가 공백으로 구분되어 있습니다.

### 입출력 예

s return
1 2 3 4 1 4
-1 -2 -3 -4 -4 -1
-1 -1 -1 -1

```js
function solution(s) {
  let answer = [];
  const newArray = s.split(" ").sort((x, y) => x - y);
  let Max = newArray.pop();
  let Min = newArray.shift();
  answer.push(Min + " " + Max);
  return answer.join();
}
```

## 다음 큰 숫자

자연수 n 이 주어졌을 때, n 의 다음 큰 숫자는 다음과 같이 정의 합니다.

조건 1. n 의 다음 큰 숫자는 n 보다 큰 자연수 입니다.
조건 2. n 의 다음 큰 숫자와 n 은 2 진수로 변환했을 때 1 의 갯수가 같습니다.
조건 3. n 의 다음 큰 숫자는 조건 1, 2 를 만족하는 수 중 가장 작은 수 입니다.
예를 들어서 78(1001110)의 다음 큰 숫자는 83(1010011)입니다.

자연수 n 이 매개변수로 주어질 때, n 의 다음 큰 숫자를 return 하는 solution 함수를 완성해주세요.

### 제한 사항

n 은 1,000,000 이하의 자연수 입니다.

### 입출력 예

n result
78 83
15 23

### 입출력 예 설명

입출력 예#1
문제 예시와 같습니다.
입출력 예#2
15(1111)의 다음 큰 숫자는 23(10111)입니다.

```js
function solution(n) {
  let preNum = Array.from(n.toString(2)).filter(item => item != 0);
  let afterNum = 0;
  while (afterNum !== preNum.length) {
    ++n;
    afterNum = Array.from(n.toString(2)).filter(item => item != 0).length;
  }
  return n;
}
```
