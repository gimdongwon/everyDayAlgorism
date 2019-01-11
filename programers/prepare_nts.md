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
