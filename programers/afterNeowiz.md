# 네오위즈 이후 1일 1알고리즘

## 위장

```js
function solution(clothes) {
  let result = 1,
    arr = [];
  for (let i = 0; i < clothes.length; i++) {
    if (!arr.includes(clothes[i][1])) {
      arr.push(clothes[i][1]);
    }
  }
  for (let i = 0; i < arr.length; i++) {
    result *= clothes.filter(item => item[1] === arr[i]).length + 1;
  }
  return result - 1;
}

// 5 + 9 + 7 + 2 = 23
```
