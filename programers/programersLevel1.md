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
