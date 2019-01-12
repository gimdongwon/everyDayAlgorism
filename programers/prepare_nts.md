# algorithm

## 같은 숫자는 싫어

```js
function solution(arr) {
  // 앞에 것이라 같으면 안넣음
  // let result = [arr[0]];
  // for(let i=1; i<arr.length; i++){
  //     arr[i]===arr[i-1] ? "" : result.push(arr[i])
  // }
  // return result;

  // 뒤에 것과 같으면 안넣음
  // let result = [];
  // for(let i=0; i<arr.length; i++){
  //     arr[i]===arr[i+1]? "": result.push(arr[i])
  // }return result

  let result = arr.filter((item, index, arr) => {
    return arr[index] !== arr[index + 1];
  });
  return result;
}
```

## 완주하지 못한 선수

```js
function solution(participant, completion) {
  // 효율성 실패
  // for(let i=0; i<completion.length; i++){
  //         participant.splice(participant.indexOf(completion[i]),1)
  // }
  // return participant.toString();
  participant.sort();
  completion.sort();
  for (let i = 0; i < participant.length; i++) {
    if (participant[i] != completion[i]) return participant[i];
  }
}
```

## 두 정수 사이의 합

```js
function solution(a, b) {
  let result = 0;
  if (a === b) return a;
  const min = Math.min(a, b);
  const max = Math.max(a, b);
  for (let i = min; i <= max; i++) {
    result += i;
  }
  return result;
}
```

## 문자열 다루기 기본

# 숫자는!!! length 값이 없다~!!!!!!

```js
function solution(s) {
  const num = parseInt(s);
  return num.length === (4 || 6) && num == s ? true : false;
}
```

# 문자열 내 p와 y 개수

```js
function solution(s) {
  let pCount = 0;
  let yCount = 0;
  let newS = s.toLowerCase().split("");
  for (let i = 0; i < newS.length; i++) {
    if (newS[i] == "p") pCount++;
    else if (newS[i] == "y") yCount++;
  }
  return pCount === yCount ? true : false;
}
function solution(s) {
  // let pCount = 0;
  // let yCount = 0;
  let newS = s.toLowerCase().split("");
  // newS.filter(item=>{
  //     item === "p" ? pCount++ : item==="y" ? yCount++ : ""
  // })
  let pCount = newS.filter(item => item === "p").length;
  let yCount = newS.filter(item => item === "y").length;
  console.log(pCount, yCount);
  return pCount === yCount ? true : false;
}
```

## 2016

```js
function solution(a, b) {
  return new Date(2016, a - 1, b)
    .toDateString()
    .slice(0, 3)
    .toUpperCase();
}
```

## 문자열 내림차순으로 정렬

```js
function solution(s) {
  return [...s]
    .sort()
    .reverse()
    .join("");
}
```

## 수박수박

```js
function solution(n) {
  let x = "수박".repeat(5000);
  return x.slice(0, n);
}
```

## 서울에서 김서방 찾기

```js
function solution(seoul) {
  return `김서방은 ${seoul.indexOf("Kim")}에 있다`;
}
```

## 소수 찾기

```js
function solution(n) {
  let token = [];
  let answer = [];
  for (let i = 2; i <= n; ++i) {
    if (!token[i]) {
      answer.push(i);
      for (let j = i * 2; j <= n; j += i) {
        token[j] = true;
      }
    }
  }
  return answer.length;
}
```

## 약수의합

```js
function solution(n) {
  let sum = 0;
  for (let i = 1; i <= n; i++) {
    if (n % i === 0) {
      sum += i;
    }
  }
  return sum;
}
```

## 문자열 내 마음대로 정렬하기

```js
function solution(strings, n) {
  return strings.sort((x, y) =>
    x[n] === y[n] ? x.localeCompare(y) : x[n].localeCompare(y[n])
  );
}
```

## 시저암호

```js
function solution(s, n) {
  // a는 97
  // z는 122
  // A는 65
  // Z는 90
  // 공백은 32
  let answer = [];
  let newChar = [...s];
  for (let i = 0; i < newChar.length; i++) {
    let newNum = newChar[i].charCodeAt() + n;
    if (newNum - n === 32) {
      answer.push(String.fromCharCode(newNum - n));
    } else {
      answer.push(
        String.fromCharCode(
          newNum - n > 90
            ? ((newNum - 97) % 26) + 97
            : ((newNum - 65) % 26) + 65
        )
      );
    }
  }
  return answer.join("");
}
```

## 행렬의 덧셈

```js
function solution(arr1, arr2) {
  for (let i = 0; i < arr1.length; i++) {
    for (let j = 0; j < arr1[i].length; j++) {
      arr1[i][j] += arr2[i][j];
    }
  }
  return arr1;
}
```

## 핸드폰 번호 가리기

```js
function solution(phone_number) {
  // let num = phone_number.split("");
  // num.splice(0, num.length-4, "*".repeat(num.length-4))
  // return num.join("")
  return phone_number.replace(/\d(?=\d{4})/g, "*");
}
```

## 가운데 글자 가져오기

```js
function solution(phone_number) {
  // let num = phone_number.split("");
  // num.splice(0, num.length-4, "*".repeat(num.length-4))
  // return num.join("")
  return phone_number.replace(/\d(?=\d{4})/g, "*");
}
```

## 나누어 떨어지는 숫자

```js
function solution(arr, divisor) {
  let result = arr.filter(item => item % divisor === 0);
  return result.length === 0 ? [-1] : result.sort((x, y) => x - y);
}
```

## 콜라츠 추측

```js
function solution(num) {
  let count = 0;
  while (num !== 1) {
    num % 2 === 0 ? (num /= 2) : (num = num * 3 + 1);
    count++;
    if (count > 500) return -1;
  }
  return count;
}
```

## 제일 작은수 찾기

```js
function solution(arr) {
  const min = Math.min(...arr);
  return arr.length === 1 ? [-1] : arr.filter(item => item !== min);
}
```

## 내림차순 배치

```js
function solution(n) {
  let a = n.toString();
  return parseInt([...a].sort((x, y) => y - x).join(""));
}
```
