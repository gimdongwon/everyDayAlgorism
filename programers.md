# 프로그래머스 알고리즘 문제

## 1

### 수박수박수박수박수박수?

water_melon함수는 정수 n을 매개변수로 입력받습니다.
길이가 n이고, 수박수박수...와 같은 패턴을 유지하는 문자열을 리턴하도록 함수를 완성하세요.

예를들어 n이 4이면 '수박수박'을 리턴하고 3이라면 '수박수'를 리턴하면 됩니다.

```js
function waterMelon(n){
  var result = ""
  let i;
  for(i = 1; i <= n; i++){
  if(i % 2 === 0){
      result += "박"
  }
      else(
      result += "수");
  }
  return result;
}

// 실행을 위한 테스트코드입니다.
console.log("n이 3인 경우: "+ waterMelon(3))
console.log("n이 4인 경우: "+ waterMelon(4))
```

## 2

### 문자열 다루기

alpha_string46함수는 문자열 s를 매개변수로 입력받습니다.
s의 길이가 4혹은 6이고, 숫자로만 구성되있는지 확인해주는 함수를 완성하세요.
예를들어 s가 a234이면 False를 리턴하고 1234라면 True를 리턴하면 됩니다

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

>나는 이문제가 왜이리 어렵지 계속 풀어보자

### 문자열 다루기

```js
function evenOrOdd(num) {
  var result = ''
  if(parseInt(num)%2===0){
    return "Even"
  }else{
      return "Odd"
  }
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + evenOrOdd(2));
console.log("결과 : " + evenOrOdd(3));
```

### 행렬의 덧셈

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다.
 2개의 행렬을 입력받는 sumMatrix 함수를 완성하여 행렬 덧셈의 결과를 반환해 주세요.
예를 들어 2x2 행렬인 A = ((1, 2), (2, 3)), B = ((3, 4), (5, 6)) 가 주어지면, 
같은 2x2 행렬인 ((4, 6), (7, 9))를 반환하면 됩니다.(어떠한 행렬에도 대응하는 함수를 완성해주세요.)

```js

function sumMatrix(A,B){

var answer = Array();
  for(var i = 0; i < A.length; i++){
    answer[i] = [];
      for(var j = 0; j < A[i].length; j++){
        answer[i][j] = A[i][j] + B[i][j];
      }
    }
  return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(sumMatrix([[1,2], [2,3]], [[3,4],[5,6]]))

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
예를 들어 12가 입력된다면 12의 약수는 [1, 2, 3, 4, 6, 12]가 되고, 총 합은 28이 되므로 28을 반환해 주면 됩니다.

```js
function sumDivisor(num) {
var answer = 0;
    let divisor;
    for(let i=1; i<=num;i++){
        if(num%i===0){
            answer += i;
        }
    }
return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(sumDivisor(12));
```