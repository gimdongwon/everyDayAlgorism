# 쇠막대기

```js
function solution(arrangement) {
  let result = 0;
  const newArr = arrangement.split("()").join(0);
  let stack = [];
  for (let i = 0; i < newArr.length; i++) {
    if (newArr[i] === "(") {
      stack.push("(");
    } else if (newArr[i] === ")") {
      stack.pop();
      result += 1;
    } else {
      result += stack.length;
    }
  }
  return result;
}
```

# 프린터

1. while문으로 맨앞의 숫자가 최상위이면 shift하고 아니면 shift해서 push함
2. while문 탈출은 내가 몇번째로 나오는지 원하는 숫자가 shift하면 종료

## 안풀린거..;;

```js
function solution(priorities, location) {
  let count = 1;
  const firstLocation = priorities[location];
  while (priorities.includes(firstLocation + 1)) {
    if (priorities.filter(item => item > priorities[0]).length) {
      priorities.push(priorities.shift());
      location > 0 ? location-- : (location = priorities.length);
    } else {
      if (firstLocation === priorities[0]) {
        return count;
      } else {
        priorities.shift();
        count++;
      }
    }
  }
}
```
