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

## 베스트 앨범

> 아직 해결 못함..
>
> plays를 직접 다루다 보니 결과값이
> 실행한 결괏값 Array [ 4, 1, 2, 0, 1, -1, 0, -1 ]이(가) 기댓값 Array [ 4, 1, 3, 0 ]와(과) 다릅니다.
>
> 가 나옴
>
> 새로운 배열로 만들어서 진행하니 시간초과 발생.. 좀더 생각해보자

```js
function solution(genres, plays) {
  // 가장 큰 값을 찾아서 넣고 잘라주고
  // 그것과 같은 종류의 음악 횟수를 index를 넣고 잘라주고
  // 같은 장류가 2개 이상이면 나머지는 싹다 거르기
  let result = [],
    beforeGen;
  while (plays.length) {
    const findMaxNum = arr => Math.max.apply(null, arr);
    const maxNum = findMaxNum(plays);
    const maxNumIdx = plays.indexOf(maxNum);

    result.push(maxNumIdx);
    beforeGen = genres[maxNumIdx];
    plays.splice(maxNumIdx, 1);
    genres.splice(maxNumIdx, 1);

    let newGenArr = [];
    genres.forEach((item, index) => {
      if (item === beforeGen) {
        newGenArr.push(index);
      }
    });
    if (newGenArr) {
      let newPlays = [];
      for (let i = 0; i < newGenArr.length; i++) {
        newPlays.push(plays[newGenArr[i]]);
      }
      const secondMaxNumIdx = result.push(plays.indexOf(findMaxNum(newPlays)));
      plays.splice(secondMaxNumIdx, 1);
      genres.splice(secondMaxNumIdx, 1);
    }
  }
  return result;
}
```
