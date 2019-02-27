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

문자열 s 에는 공백으로 구분된 숫자들이 저장되어 있습니다. str 에 나
나는 숫자 중 최소값과 최대값을 찾아 이를 (최소값) (최대값)형태의 문자열을 반환하는 함수, solution 을 완성하세요.
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

## 최솟값 만들기

### 문제 설명

길이가 같은 배열 A, B 두개가 있습니다. 각 배열은 자연수로 이루어져 있습니다.
배열 A, B 에서 각각 한 개의 숫자를 뽑아 두 수를 곱합니다. 이러한 과정을 배열의 길이만큼 반복하며, 두 수를 곱한 값을 누적하여 더합니다. 이때 최종적으로 누적된 값이 최소가 되도록 만드는 것이 목표입니다. (단, 각 배열에서 k 번째 숫자를 뽑았다면 다음에 k 번째 숫자는 다시 뽑을 수 없습니다.)

예를 들어 A = [1, 4, 2] , B = [5, 4, 4] 라면

A 에서 첫번째 숫자인 1, B 에서 두번째 숫자인 5 를 뽑아 곱하여 더합니다. (누적된 값 : 0 + 5(1x5) = 5)
A 에서 두번째 숫자인 4, B 에서 세번째 숫자인 4 를 뽑아 곱하여 더합니다. (누적된 값 : 5 + 16(4x4) = 21)
A 에서 세번째 숫자인 2, B 에서 첫번째 숫자인 4 를 뽑아 곱하여 더합니다. (누적된 값 : 21 + 8(2x4) = 29)
즉, 이 경우가 최소가 되므로 29 를 return 합니다.

배열 A, B 가 주어질 때 최종적으로 누적된 최솟값을 return 하는 solution 함수를 완성해 주세요.

### 제한사항

배열 A, B 의 크기 : 1000 이하의 자연수
배열 A, B 의 원소의 크기 : 1000 이하의 자연수

### 입출력 예

A B answer
[1, 4, 2][5, 4, 4] 29
[1,2][3,4] 10

### 입출력 예 설명

입출력 예 #1
문제의 예시와 같습니다.

입출력 예 #2
A 에서 첫번째 숫자인 1, B 에서 두번째 숫자인 4 를 뽑아 곱하여 더합니다. (누적된 값 : 4) 다음, A 에서 두번째 숫자인 2, B 에서 첫번째 숫자인 3 을 뽑아 곱하여 더합니다. (누적된 값 : 4 + 6 = 10)
이 경우가 최소이므로 10 을 return 합니다.

```js
function solution(A, B) {
  var answer = 0;
  const newA = A.sort(function(a, b) {
    return a - b;
  });
  const newB = B.sort(function(a, b) {
    return b - a;
  });
  for (let i = 0; i < A.length; i++) {
    answer += newA[i] * newB[i];
  }

  return answer;
}
```

## 올바른 괄호

### 문제 설명

올바른 괄호란 두 개의 괄호 '(' 와 ')' 만으로 구성되어 있고, 괄호가 올바르게 짝지어진 문자열입니다. 괄호가 올바르게 짝지어졌다는 것은 '(' 문자로 열렸으면 반드시 짝지어서 ')' 문자로 닫혀야 합니다.
예를들어

()() 또는 (())() 는 올바른 괄호입니다.
)()( 또는 (()( 는 올바르지 않은 괄호입니다.
'(' 또는 ')' 로만 이루어진 문자열 s 가 주어졌을 때, 문자열 s 가 올바른 괄호이면 true 를 return 하고, 올바르지 않은 괄호이면 false 를 return 하는 solution 함수를 완성해 주세요.

### 제한사항

문자열 s 의 길이 : 100,000 이하의 자연수
문자열 s 는 '(' 또는 ')' 로만 이루어져 있습니다.

### 입출력 예

s answer
()() true
(())() true
)()( false
(()( false

### 입출력 예 설명

입출력 예 #1,2,3,4
문제의 예시와 같습니다.

```js
function solution(s) {
  let newStr = s.split("");
  let num = 0;
  for (let i = 0; i < newStr.length; i++) {
    if (newStr[0] == ")" || newStr[newStr.length - 1] == "(") {
      return false;
    } else if (newStr[i] == "(") {
      num++;
    } else if (newStr[i] == ")") {
      num--;
      if (num < 0) {
        return false;
      }
    }
  }
  return num == 0 ? true : false;
}
```

## 124 나라의 숫자

```js
function solution(n) {
  let answer = [];

  while (n > 0) {
    let countNum = n % 3;
    n = Math.floor(n / 3);
    if (countNum === 0) {
      n = n - 1;
    }
    answer.unshift(countNum);
  }
  return answer.join("").replace(/0/gi, "4");
}
```

## 숫자의 표현

```js
function solution(num) {
  let answer = 0,
    sum = 0,
    j;
  for (let i = 1; i <= num; i++) {
    (sum = 0), (j = i);
    while (sum <= num) {
      sum += j;
      if (sum === num) answer++;
      j++;
    }
  }
  return answer;
}

function solution(num) {
  let answer = 0;
  for (let i = 1; i <= num; i++) {
    if (num % i == 0 && i % 2 == 1) {
      // 뭐냐ㅠ
      answer++;
    }
  }
  return answer;
}
```

## 쇠막대기

```js
function solution(arrangement) {
  let stack = [];
  let result = 0;
  const newArr = [...arrangement];
  for (let i = 0; i < newArr.length; i++) {
    if (newArr[i] === "(") {
      stack.push("(");
    } else {
      if (newArr[i - 1] === "(") {
        stack.pop();
        result += stack.length;
      } else {
        result += 1;
        stack.pop();
      }
    }
  }
  return result;
}
```

## 탑

```js
function solution(heights) {
  let result = [];
  // 앞의 값이 현재 값보다 큰지 안큰지 비교후
  // 크면 앞의 값 index를 넣고
  // 안크면 앞앞의 값을 보고 반복
  for (let i = heights.length - 1; i > -1; i--) {
    let j = i - 1;
    while (heights[i] > heights[j]) {
      if (j == -1) {
        break;
      }
      j--;
    }
    heights[i] < heights[j] ? result.unshift(j + 1) : result.unshift(0);
  }
  return result;
}
```

## 124

```js
function solution(n) {
  let result = [];
  while (n > 0) {
    if (n % 3 === 0) {
      n = n - 1;
      result.unshift("4");
    } else if (n % 3 === 1) {
      result.unshift("1");
    } else {
      result.unshift("2");
    }
    n = Math.floor(n / 3);
  }
  return result.join("");
}
```

## 다음 큰 숫자

알게된 것

정규표현식 match는 내가 원하는 값을 적어서 맞춰줄 수 있음 `match(/1/gi)`

```js
function solution(n, a = n + 1) {
  return n.toString(2).match(/1/gi).length === a.toString(2).match(/1/gi).length
    ? a
    : solution(a, a + 1);
}

function solution(n) {
  let count = 0;
  let result = n.toString(2);
  for (let i = 0; i < result.length; i++) {
    if (result[i] === "1") {
      count++;
    }
  }
  let target;
  while (count !== target) {
    target = 0;
    n++;
    result = n.toString(2);
    for (let i = 0; i < result.length; i++) {
      if (result[i] === "1") {
        target++;
      }
    }
  }
  return n;
}
```

## 스킬트리

```js
function solution(skill, skill_trees) {
    let skillArr = [...skill], result = [];
    // 스킬의 인덱스가 그 다음 스킬의 인덱스보다 크면 탈락
    for(let i=0; i<skillArr.length; i++){
        for(let j=0; j<skill_trees.length; j++){
            skill_trees[j] = skill_trees[j].replace(skillArr[i], i+1);
        }
    }
    for(let i=0; i<skill_trees.length; i++){
        let origin = skill_trees[i].match(/\d/g).join("")
        let newArr = skill_trees[i].match(/\d/g).sort((x,y)=> x-y).join("");
        if(origin==newArr){
            let j=1;
            if(origin.includes(j)){
               result.push(origin)
               }
        }
    }
    return result.length
}
런타임에러..
```

## 기능 개발

```js
function solution (progresses, speeds){
    let result = [], k=0, acc=0;
    while(progresses.some(item=> item<100)){
        for(let i=0; i<progresses.length; i++){
            progresses[i]+=speeds[i]
        }
        if(progresses[k]>=100){
            k++,acc++
            if(k<progresses.length){
                while(progresses[k]>=100){
                    k++, acc++
                    if(progresses[k]<100){
                        result.push(acc)
                        acc = 0
                    }
                }
                if(acc!==0&&progresses[k]<100){
                        result.push(acc)
                        acc = 0
                    }
            }
            if(k>=progresses.length){
                result.push(acc)
            }
        }
    }
    return result
}
```

> 어거지로 풀었다.. 모든 케이스들 확인하면서.. 이런 경우도 풀 수 있는 능력을 기르자!

> 다른 풀이들도 엄청 깔끔한건 없었고 대부분 이런 식으로 해결하였다. 다만 접근방식이 조금 다를뿐!