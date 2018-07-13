# 프로그래머스 알고리즘 문제

## 1

### 수박수박수박수박수박수?

water_melon 함수는 정수 n 을 매개변수로 입력받습니다.
길이가 n 이고, 수박수박수...와 같은 패턴을 유지하는 문자열을 리턴하도록 함수를 완성하세요.

예를들어 n 이 4 이면 '수박수박'을 리턴하고 3 이라면 '수박수'를 리턴하면 됩니다.

```js
function waterMelon(n) {
  var result = "";
  let i;
  for (i = 1; i <= n; i++) {
    if (i % 2 === 0) {
      result += "박";
    } else result += "수";
  }
  return result;
}

// 실행을 위한 테스트코드입니다.
console.log("n이 3인 경우: " + waterMelon(3));
console.log("n이 4인 경우: " + waterMelon(4));
```

## 2

### 문자열 다루기

alpha_string46 함수는 문자열 s 를 매개변수로 입력받습니다.
s 의 길이가 4 혹은 6 이고, 숫자로만 구성되있는지 확인해주는 함수를 완성하세요.
예를들어 s 가 a234 이면 False 를 리턴하고 1234 라면 True 를 리턴하면 됩니다

```js
실패코드 ㅠㅠ
function alpha_string46(s){
  var result = true;
  if(s.length === 4 || s.length === 6){
      return s.split('').every(item=>parseInt(item)== Number );
  }else(
  return false;
  );
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log( alpha_string46("a234") );
```

> 나는 이문제가 왜이리 어렵지 계속 풀어보자

### 문자열 다루기

```js
function evenOrOdd(num) {
  var result = "";
  if (parseInt(num) % 2 === 0) {
    return "Even";
  } else {
    return "Odd";
  }
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + evenOrOdd(2));
console.log("결과 : " + evenOrOdd(3));
```

### 행렬의 덧셈

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다.
2 개의 행렬을 입력받는 sumMatrix 함수를 완성하여 행렬 덧셈의 결과를 반환해 주세요.
예를 들어 2x2 행렬인 A = ((1, 2), (2, 3)), B = ((3, 4), (5, 6)) 가 주어지면,
같은 2x2 행렬인 ((4, 6), (7, 9))를 반환하면 됩니다.(어떠한 행렬에도 대응하는 함수를 완성해주세요.)

```js
function sumMatrix(A, B) {
  var answer = Array();
  for (var i = 0; i < A.length; i++) {
    answer[i] = [];
    for (var j = 0; j < A[i].length; j++) {
      answer[i][j] = A[i][j] + B[i][j];
    }
  }
  return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(sumMatrix([[1, 2], [2, 3]], [[3, 4], [5, 6]]));
```

### 뭐지? parseInt

```js
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다.
 2개의 행렬을 입력받는 sumMatrix 함수를 완성하여 행렬 덧셈의 결과를 반환해 주세요.
예를 들어 2x2 행렬인 A = ((1, 2), (2, 3)), B = ((3, 4), (5, 6)) 가 주어지면, 같은 2x2 행렬인 ((4, 6), (7, 9))를 반환하면 됩니다.(어떠한 행렬에도 대응하는 함수를 완성해주세요.)
```

### 약수 합하기

Level 1
어떤 수를 입력받아 그 수의 약수를 모두 더한 수 sumDivisor 함수를 완성해 보세요.
예를 들어 12 가 입력된다면 12 의 약수는 [1, 2, 3, 4, 6, 12]가 되고, 총 합은 28 이 되므로 28 을 반환해 주면 됩니다.

```js
function sumDivisor(num) {
  var answer = 0;
  let divisor;
  for (let i = 1; i <= num; i++) {
    if (num % i === 0) {
      answer += i;
    }
  }
  return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(sumDivisor(12));
```

### 역삼각형 출력하기

printReversedTriangle 메소드는 양의 정수 num 을 매개변수로 입력받습니다.
다음을 참고해 \*(별)로 높이가 num 인 삼각형을 문자열로 리턴하는 printReversedTriangle 메소드를 완성하세요

높이(num)가 3 일때 다음과 같은 문자열을 리턴하면 됩니다.

```js
***
**
*
```

```js
function printReversedTriangle(num) {
  var result = "";
  // 함수를 완성하세요
  for (let i = num; i > 0; i--) {
    result += "*".repeat(i) + `\n`;
  }
  return result;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + "\n" + printReversedTriangle(3));
```

### 김서방 찾기

findKim 함수(메소드)는 String 형 배열 seoul 을 매개변수로 받습니다.

seoul 의 element 중 Kim 의 위치 x 를 찾아, 김서방은 x 에 있다는 String 을 반환하세요.
seoul 에 Kim 은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.

```js
function findKim(seoul) {
  var idx = 0;
  //함수를 완성하세요
  idx = seoul.indexOf("Kim");
  return "김서방은 " + idx + "에 있다";
}

// 실행을 위한 테스트코드입니다.
console.log(findKim(["Queen", "Tod", "Kim"]));
```

### 평균구하기

함수를 완성해서 매개변수 array 의 평균값을 return 하도록 만들어 보세요.
어떠한 크기의 array 가 와도 평균값을 구할 수 있어야 합니다.

```js
function average(array) {
  //함수를 완성하세요

  return array.reduce((item, acc) => item + acc, 0) / array.length;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
var testArray = [5, 3, 4];
console.log("평균값 : " + average(testArray));
```

### 별찍기

printTriangle 메소드는 양의 정수 num 을 매개변수로 입력받습니다.
다음을 참고해 \*(별)로 높이가 num 인 삼각형을 문자열로 리턴하는 printTriangle 메소드를 완성하세요
printTriangle 이 return 하는 String 은 개행문자('\n')로 끝나야 합니다.

```
높이가 3일때

*
**
***
높이가 5일때

*
**
***
****
*****
```

```js
function printTriangle(num) {
  let result = "";
  for (let i = 1; i <= num; i++) {
    result += "*".repeat(i) + "\n";
  }
  return result;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(printTriangle(3));
```

### 핸드폰 번호 가리기

별이는 헬로월드텔레콤에서 고지서를 보내는 일을 하고 있습니다. 개인정보 보호를 위해 고객들의 전화번호는 맨 뒷자리 4 자리를 제외한 나머지를 "\*"으로 바꿔야 합니다.
전화번호를 문자열 s 로 입력받는 hide_numbers 함수를 완성해 별이를 도와주세요
예를들어 s 가 "01033334444"면 "**\*\*\***4444"를 리턴하고, "027778888"인 경우는 "**\***8888"을 리턴하면 됩니다.

```js
function hide_numbers(s) {
  //함수를 완성해주세요
  return "*".repeat(s.length - 4) + s.slice(s.length - 4, s.length);
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + hide_numbers("01033334444"));
```

### 문자열 내의 p,y 의 갯수

numPY 함수는 대문자와 소문자가 섞여있는 문자열 s 를 매개변수로 입력받습니다.
s 에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False 를 리턴하도록 함수를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True 를 리턴합니다.
예를들어 s 가 pPoooyY 면 True 를 리턴하고 Pyy 라면 False 를 리턴합니다.

```js
function numPY(s) {
  let pCount = 0;
  let yCount = 0;
  for (let i = 0; i < s.length; i++) {
    if (s[i] === "p") {
      pCount++;
    } else if (s[i] === "P") {
      pCount++;
    } else if (s[i] === "y") {
      yCount++;
    } else if (s[i] === "Y") {
      yCount++;
    }
  }
  if (pCount === yCount) {
    return true;
  } else {
    return false;
  }
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(numPY("pPoooyY"));
console.log(numPY("Pyy"));
```

## 정수제곱근 구하기

nextSqaure 함수는 정수 n 을 매개변수로 입력받습니다.
n 이 임의의 정수 x 의 제곱이라면 x+1 의 제곱을 리턴하고, n 이 임의의 정수 x 의 제곱이 아니라면 'no'을 리턴하는 함수를 완성하세요.
예를들어 n 이 121 이라면 이는 정수 11 의 제곱이므로 (11+1)의 제곱인 144 를 리턴하고, 3 이라면 'no'을 리턴하면 됩니다.

```js
function nextSqaure(n) {
  root = Math.sqrt(n);
  return Number.isInteger(root) ? Math.pow(root + 1, 2) : "no";
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + nextSqaure(121));
```

## 피보나치 수

피보나치 수는 F(0) = 0, F(1) = 1 일 때, 2 이상의 n 에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 점화식입니다. 2 이상의 n 이 입력되었을 때, fibonacci 함수를 제작하여 n 번째 피보나치 수를 반환해 주세요. 예를 들어 n = 3 이라면 2 를 반환해주면 됩니다.

```js
function fibonacci(num) {
  return num < 2 ? num : fibonacci(num - 1) + fibonacci(num - 2);
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(fibonacci(6));
```

## 문자열 다루기

alpha_string46 함수는 문자열 s 를 매개변수로 입력받습니다.
s 의 길이가 4 혹은 6 이고, 숫자로만 구성되있는지 확인해주는 함수를 완성하세요.
예를들어 s 가 a234 이면 False 를 리턴하고 1234 라면 True 를 리턴하면 됩니다

```js
function alpha_string46(s) {
  const newArray = Array.from(s);
  let count = 0;
  for (let i = 0; i < s.length; i++) {
    const newNum = parseInt(newArray[i]);
    if (Number.isInteger(newNum)) {
      if (s.length === 4 || s.length === 6) {
        if (count === s.length - 1) {
          return true;
        } else {
          count += 1;
        }
      } else return false;
    } else {
      return false;
    }
  }
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(alpha_string46("a234"));
console.log(alpha_string46("3456"));
```

## 정수 내림차순으로 배치하기

문제 설명

함수 solution 은 정수 n 을 매개변수로 입력받습니다. n 의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n 이 118372 면 873211 을 리턴하면 됩니다.

### 제한 조건

- n 은 1 이상 8000000000 이하인 자연수입니다.

### 입출력 예

| n | return |

| 118372 | 873211 |

```js
function solution(n) {
  return parseInt(
    n
      .toString()
      .split("")
      .sort()
      .reverse()
      .join("")
  );
}
solution(118372);
```

## 문자열 내 마음대로 정렬하기

문자열로 구성된 리스트 strings 와, 정수 n 이 주어졌을 때, 각 문자열의 인덱스 n 번째 글자를 기준으로 오름차순 정렬하려 합니다. 예를 들어 strings 가 [sun, bed, car]이고 n 이 1 이면 각 단어의 인덱스 1 의 문자 u, e, a 로 strings 를 정렬합니다.

### 제한 조건

strings 는 길이 1 이상, 50 이하인 배열입니다.
strings 의 원소는 소문자 알파벳으로 이루어져 있습니다.
strings 의 원소는 길이 1 이상, 100 이하인 문자열입니다.
모든 strings 의 원소의 길이는 n 보다 큽니다.
인덱스 1 의 문자가 같은 문자열이 여럿 일 경우, 사전순으로 앞선 문자열이 앞쪽에 위치합니다.

### 입출력 예

strings n return
[sun, bed, car] 1 [car, bed, sun][abce, abcd, cdx] 2 [abcd, abce, cdx]
입출력 예 설명
입출력 예 1
sun, bed, car 의 1 번째 인덱스 값은 각각 u, e, a 입니다. 이를 기준으로 strings 를 정렬하면 [car, bed, sun] 입니다.

### 입출력 예 2

abce 와 abcd, cdx 의 2 번째 인덱스 값은 c, c, x 입니다. 따라서 정렬 후에는 cdx 가 가장 뒤에 위치합니다. abce 와 abcd 는 사전순으로 정렬하면 abcd 가 우선하므로, 답은 [abcd, abce, cdx] 입니다.

```js
실패함;
function solution(strings, n) {
  let newList = [];
  let compareList = [];
  let resultList = [];
  for (let i = 0; i < strings.length; i++) {
    newList.push(strings[i][n]);
    compareList.push(strings[i][n]);
  }
  let newCompareList = compareList.sort();
  for (let i = 0; i < strings.length; i++) {
    if (newCompareList[i] === newCompareList[i + 1]) {
      let lastList = [strings[i], strings[i + 1]].sort();
      resultList.push(lastList[0], lastList[1]);
      i++;
    } else {
      resultList.push(strings[newList.indexOf(newCompareList[i])]);
    }
  }
  return resultList;
}
```

## 제일 작은 수 제거하기

정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution 을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1 을 채워 리턴하세요. 예를들어 arr 이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

### 제한 조건

arr 은 길이 1 이상인 배열입니다.
인덱스 i, j 에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.

### 입출력 예

arr return
[4,3,2,1][4,3,2]
[10][-1]

```js
function solution(arr) {
  const min = Math.min(...arr);
  return arr.length !== 1 ? arr.filter(i => i !== min) : [-1];
}
```

## 문자열 내림차순으로 배치하기

문자열 s 에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution 을 완성해주세요.
s 는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.

### 제한 사항

str 은 길이 1 이상인 문자열입니다.

### 입출력 예

s return
Zbcdefg gfedcbZ

```js
function solution(s) {
  return [...s]
    .sort()
    .reverse()
    .join("");
}
```

## 같은 숫자는 싫어

문제 설명
배열 arr 가 주어집니다. 배열 arr 의 각 원소는 숫자 0 부터 9 까지로 이루어져 있습니다. 이때, 배열 arr 에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 배열 arr 에서 제거 되고 남은 수들을 return 하는 solution 함수를 완성해 주세요. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr 의 원소들의 순서를 유지해야 합니다.
예를들면

arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
배열 arr 에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

### 제한사항

배열 arr 의 크기 : 1,000,000 이하의 자연수
배열 arr 의 원소의 크기 : 0 보다 크거나 같고 9 보다 작거나 같은 정수

### 입출력 예

arr answer
[1,1,3,3,0,1,1][1,3,0,1]
[4,4,4,3,3][4,3]

### 입출력 예 설명

입출력 예 #1,2
문제의 예시와 같습니다.

```js
function solution(s) {
  let before;
  const newArray = [];
  for (let i = 0; i < s.length; i++) {
    if (before !== s[i]) {
      newArray.push(s[i]);
    }
    before = s[i];
  }
  return newArray;
}
```

## 2016 년

### 문제 설명

2016 년 1 월 1 일은 금요일입니다. 2016 년 a 월 b 일은 무슨 요일일까요? 두 수 a ,b 를 입력받아 2016 년 a 월 b 일이 무슨 요일인지 리턴하는 함수, solution 을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT

입니다. 예를 들어 a=5, b=24 라면 5 월 24 일은 화요일이므로 문자열 TUE 를 반환하세요.

### 제한 조건

2016 년은 윤년입니다.
2016 년 a 월 b 일은 실제로 있는 날입니다. (13 월 26 일이나 2 월 45 일같은 날짜는 주어지지 않습니다)

### 입출력 예

a b result
5 24 TUE

```js
// 1,2,3,4,5,6,7,8,9,10,11,12
// 31,29,31,30,31,30,31,31,30,31,30,31

// 1month = 31
// 2month = 60
// 3month = 91
// 4month = 121
// 5month = 152
// 6month = 182
// 7month = 213
// 8month = 244
// 9month = 274
// 10month = 305
// 11month = 335
// 12month = 365

// 5month 4day
// month + day = 152 + 4 = 156

// 156 % 7 = 2 => sunday
// %7 = 1 => saturday
// %7 = 2 => sunday
// %7 = 3 => monday
// %7 = 4 => tuesday
// %7 = 5 => wednesday
// %7 = 6 => thursday
// %7 = 7 => firday

// 0< month <13
// 0< day < 32

// 1,3,5,7,8,10,12 는 31일
// 2 29일
// 4,6,9,11 30일

function solution(month, day) {
  let transMonth;
  let sum;
  let answer = "";
  if (day > 31 || day < 1) {
    return answer;
  } else {
    switch (month) {
      case (month = 1):
        transMonth = day;
        sum = transMonth % 7;
        break;

      case (month = 3):
        transMonth = day + 60;
        sum = transMonth % 7;
        break;

      case (month = 5):
        transMonth = day + 121;
        sum = transMonth % 7;
        break;

      case (month = 7):
        transMonth = day + 182;
        sum = transMonth % 7;
        break;

      case (month = 8):
        transMonth = day + 213;
        sum = transMonth % 7;
        break;

      case (month = 10):
        transMonth = day + 274;
        sum = transMonth % 7;
        break;

      case (month = 12):
        transMonth = day + 335;
        sum = transMonth % 7;
        break;

      case (month = 2):
        if (day < 30) {
          transMonth = day + 31;
          sum = transMonth % 7;
          break;
        } else {
          return answer;
        }

      case (month = 6):
        if (day < 31) {
          transMonth = day + 152;
          sum = transMonth % 7;
          break;
        } else {
          return answer;
        }
      case (month = 9):
        if (day < 31) {
          transMonth = day + 244;
          sum = transMonth % 7;
          break;
        } else {
          return answer;
        }

      case (month = 4):
        if (day < 31) {
          transMonth = day + 91;
          sum = transMonth % 7;
          break;
        } else {
          return answer;
        }

      case (month = 11):
        if (day < 31) {
          transMonth = day + 305;
          sum = transMonth % 7;
          break;
        } else {
          return answer;
        }
    }

    switch (sum) {
      case (sum = 1):
        answer = "FRI";
        break;

      case (sum = 2):
        answer = "SAT";
        break;

      case (sum = 3):
        answer = "SUN";
        break;

      case (sum = 4):
        answer = "MON";
        break;

      case (sum = 5):
        answer = "TUE";
        break;

      case (sum = 6):
        answer = "WED";
        break;

      case (sum = 0):
        answer = "THR";
        break;
    }
    return answer;
  }
}

solution(5, 24);
```

```js
function solution(a, b) {
  return new Date(2016, a - 1, b)
    .toDateString()
    .slice(0, 3)
    .toUpperCase();
}
```

## 자릿수 더하기

### 문제 설명

자연수 N 이 주어지면, N 의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123 이면 1 + 2 + 3 = 6 을 return 하면 됩니다.

### 제한사항

N 의 범위 : 100,000,000 이하의 자연수

### 입출력 예

N answer
123 6
987 24

### 입출력 예 설명

입출력 예 #1
문제의 예시와 같습니다.

입출력 예 #2
9 + 8 + 7 = 24 이므로 24 를 return 하면 됩니다.

```js
function solution(n) {
  let num = n.toString().split("");
  let sum = 0;
  for (let i = 0; i < num.length; i++) {
    sum += parseInt(num[i]);
  }
  return sum;
}
```

## 가운데 글자 가져오기

### 문제 설명

단어 s 의 가운데 글자를 반환하는 함수, solution 을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

### 재한사항

s 는 길이가 1 이상, 100 이하인 스트링입니다.

### 입출력 예

s return
abcde c
qwer we

```js
function solution(s) {
  return s.length % 2 !== 0
    ? s.slice(Math.trunc(s.length / 2), Math.trunc(s.length / 2) + 1)
    : s.slice(Math.trunc(s.length / 2) - 1, Math.trunc(s.length / 2) + 1);
}
```
## 소수 찾기

### 문제 설명

1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.
(1은 소수가 아닙니다.)

### 제한 조건

n은 2이상 1000000이하의 자연수입니다.

### 입출력 예
n	result
10	4
5	3

### 입출력 예 설명

입출력 예 #1
1부터 10 사이의 소수는 [2,3,5,7] 4개가 존재하므로 4를 반환

입출력 예 #2
1부터 5 사이의 소수는 [2,3,5] 3개가 존재하므로 3를 반환

```js
풀긴 했으나 시간 초과가 나왔다... 효율성 부분에서 떨어지는듯
function solution(n) {
    let result=0;
    for(let i=2; i<=n;i++){
        let divisionPoint=0;
        for (let j=2; j<=i; j++){
            if(i%j===0){
                divisionPoint+=1;
                if(i===j&&divisionPoint===1){
                    result+=1;
                }
            }
        }
    }
    return result;
}
```