# kakao blind test prepatation

## level 1

### 2016 년

```js
function 2016(a,b){
  return new Date(2016, a-1, b).toString().slice(0,3).toUpperCase();
}
```

### 가운데 글자 가져오기

```js
function solution(a) {
  const aLeng = a.length / 2;
  return a.length % 2 === 0
    ? a.slice(aLeng - 1, aLeng + 1)
    : a.slice(Math.trunc(aLeng), Math.trunc(aLeng) + 1);
}
```

### 같은 숫자는 싫어

```js
function solution(arr) {
  let result = [];
  result.push(arr[0]);
  for (let i = 1; i < arr.length; i++) {
    if (arr[i] !== arr[i - 1]) {
      result.push(arr[i]);
    }
  }
  return result;
}
```

### 나누어 떨어지는 숫자 배열

```js
function solution(arr, n) {
  let answer = [];
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] % n === 0) {
      answer.push(arr[i]);
    }
  }
  return answer[0] === undefined ? [-1] : answer.sort((x, y) => x - y);
}
```

### 두 정수 사한의 합

```js
function solution(a, b) {
  let answer = 0;
  let Min, Max;
  a < b ? ((Min = a), (Max = b)) : ((Min = b), (Max = a));
  if (a == b) return a;
  for (let i = Min; i <= Max; i++) {
    answer += i;
  }
  return answer;
}
```

### 문자열 내 p 와 y 의 갯수

```js
function solution(s) {
  let pCount = 0,
    yCount = 0;
  const newS = Array.from(s);
  for (let i = 0; i < s.length; i++) {
    if (newS[i] == "p" || newS[i] == "P") pCount++;
    else if (newS[i] == "y" || newS[i] == "Y") yCount++;
  }
  console.log(pCount);
  return pCount === yCount || (pCount === 0 && yCount === 0) ? true : false;
}
```

### 문자열 내림차순으로 배치하기

```js
function solution(s) {
  return [...s]
    .sort((x, y) => x - y)
    .reverse()
    .join("");
}
```

### 문자열 다루기 기본

```js
function solution(s) {
  if (s.length !== (4 || 6)) return false;
  const temp = parseInt(s);
  return s == temp ? true : false;
}
```

### 서울에서 김서방 찾기

```js
function solution(seoul) {
  for (let i = 0; i < seoul.length; i++) {
    if (seoul[i] === "Kim") return `김서방은 ${i}에 있다`;
  }
}

function solution(seoul) {
  return `김서방은 ${seoul.indexOf("Kim")}에 있다`;
}
```

### 소수찾기

```js
// 에라토스테네스의 체
function solution(n) {
  let newArray = [];
  let result;
  for (let i = 1; i <= n; i++) {
    newArray.push(i);
  }
  for (let j = 2; j <= n; j++) {
    if (newArray.includes(j)) {
      result = newArray.filter(item => item % j !== 0);
    }
  }
  return result;
}
```

### 수박수박수박수박수박수박수박수박수박

```js
function solution(n) {
  return n % 2 === 0
    ? "수박".repeat(n / 2)
    : "수박".repeat(Math.ceil(n / 2)).slice(0, Math.ceil(n));
}

function solution(n) {
  return "수박".repeat(n / 2) + (n % 2 ? "수" : "");
}

function solution(n) {
  return "수박".repeat(n).slice(0, n);
}
```

### 문자열 정수로 바꾸기

```js
const solution = s => parseInt(s);
```

### 약수의 합

```js
const solution = n => {
  let answer = 0;
  for (let i = 1; i <= n; i++) {
    if (n % i === 0) answer += i;
  }
  return answer;
};
```

### 시저암호

```js
const solution = (s, n) => {
  let result = [];
  const newChar = s.split("");
  for (let i = 0; i < s.length; i++) {
    let newNum = newChar[i].charCodeAt();
    if (newNum !== 32 && newNum <= 90) {
      result.push(
        String.fromCharCode(newNum + n > 90 ? newNum + n - 26 : newNum + n)
      );
    } else if (newNum !== 32 && newNum <= 122) {
      result.push(
        String.fromCharCode(newNum + n > 122 ? newNum + n - 26 : newNum + n)
      );
    } else {
      result.push(" ");
    }
  }
  return result.join("");
};
```

### 이상한 문자 만들기

```js
const solution = s => {
  let answer = [];
  let newStr = [...s];
  answer.push(newStr[0].toUpperCase());
  for (let i = 1; i < newStr.length; i++) {
    // 이전것에 따라서 다음거를 업데이트 방식
    // 그전것이 소문자이거나 빈칸이면 대문자
    // 그전것이 대문자 이면 소문자
    const newNum = answer[i - 1].charCodeAt();
    if (newNum > 64 && newNum < 91) {
      answer.push(newStr[i].toLowerCase());
    } else if (answer[i - 1] === " " || (newNum > 96 && newNum < 123)) {
      answer.push(newStr[i].toUpperCase());
    } else if (newStr[i] === " ") answer.push(" ");
  }
  return answer.join("");
};
```

## 자릿수 더하기

```js
const solution = n => {
  const newN = n.toString().split("");
  let answer = 0;
  for (let i = 0; i < newN.length; i++) {
    answer += parseInt(newN[i]);
  }
  return answer;
};
```

### 자연수 뒤집어 배열로 만들기

```js
function solution(n) {
  return Array.from(n.toString())
    .reverse()
    .map(item => parseInt(item));
}
```

### 정수 내림차순으로 정리하기

```js
const solution = n => {
  return parseInt(
    Array.from(n.toString())
      .sort((x, y) => y - x)
      .join("")
  );
};
```

### 정수 제곱근 판별

```js
const solution = n => {
  return Number.isInteger(Math.sqrt(n))
    ? Math.trunc((Math.sqrt(n) + 1) ** 2)
    : -1;
};
```

### 가장 작은수 제거하기

```js
const solution = arr => {
  const min = Math.min(...arr);
  return arr.length !== 1 ? arr.filter(i => i !== min) : [-1];
};
```
