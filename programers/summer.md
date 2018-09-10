# summer coding

## 숫자게임

```js
const solution = (A, B) => {
  let result = 0;
  let i = 0,
    j = 0;
  A = A.sort((x, y) => y - x);
  B = B.sort((x, y) => y - x);
  while (1) {
    if (B[i] > A[j]) {
      result++;
      i++;
    }
    j++;
    if (A.length <= j) break;
  }
  return result;
};
```
