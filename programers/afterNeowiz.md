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

> 이렇게해도 안되네.. 라고 찾아보니 조건을 잘못 기입했다..
>
> 전체 재생횟수를 더해서 가장 높은 장르부터 트는 것이었다.
> 그래도 많이 접근했다. 코드는 구현해놓았으니 내일 다시보자.
> 거의 2시간 했네

```js
const solution = (genres, plays) => {
  let result = [],
    nowPlayList = [...plays],
    count = 0;
  while (nowPlayList.length && genres.length) {
    let maxNum = Math.max.apply(null, nowPlayList);
    let nowIdx = plays.indexOf(maxNum);
    result.push(nowIdx);
    nowIdx = nowPlayList.indexOf(maxNum);
    nowPlayList.splice(nowIdx, 1);
    const nowGenres = genres.splice(nowIdx, 1).join();
    if (genres.includes(nowGenres)) {
      const genList = genres.reduce((acc, item, index) => {
        if (item === nowGenres) {
          acc.push(nowPlayList[index]);
        }
        return acc;
      }, []);
      nowIdx = plays.indexOf(Math.max.apply(null, genList));
      result.push(nowIdx);
      genres.splice(nowIdx, 1);
      nowPlayList.splice(nowIdx, 1);
      if (genres.includes(nowGenres)) {
        genres = genres.filter(item => item !== nowGenres);
      }
    }
    console.log(genres, nowPlayList, result);
  }
  return result;
};
```

> 드디어 해결했다!! 4일 걸렸다. Level3 클리어!

## 기능개발 Level2

```js
function solution(progresses, speeds) {
  // progresses에서 처음 인수가 100% 되었을 때의 날짜를 카운팅하여
  // 100되면 acc를 더해주고 그 다음 것이 speeds + progresses인수를 넣어 계산했을 때
  // 100이 넘거나 같으면 acc를 더해주는 방식으로 진행한다.
  let result = [],
    days = 0,
    acc = 0;
  for (let i = 0; i < speeds.length; i++) {
    let workPercent = progresses[i] + speeds[i] * days;
    while (workPercent < 100) {
      workPercent += speeds[i];
      days++;
    }
    acc++;
    function check(k) {
      if (progresses[k] + speeds[k] * days >= 100) {
        acc++;
        i++;
        check(k + 1);
      } else {
        result.push(acc);
        acc = 0;
      }
    }
    // 그 다음 progresses return 값을 살펴보고 100 넘으면 acc ++ 아니면 result에 push
    check(i + 1);
  }
  return result;
}
```

## Level_1 test

> 처음에 도전 실패했다. 첫 번째 문제들은
>
> 1. string 중간의 값을 비교하는 문제
> 2. 모의고사 문제였다.
>    첫번째 문제는 localeCompare로 간단히 풀리는 문제를 굉장히 어렵게 풀었다. reduce 사용하면서 이렇게 접근하는 법이 좋치 않은 것 같다. 하지만 어떻게든 풀어내긴해야지! 시간을 단축하자.
>    모의고사 문제는 생각을 떠올리지 못했다. 느낌은 알았는데.. 좀 더 알고리즘 적으로 생각하자.

> 그 다음 도전으로는
>
> 1. 배열의 덧셈
> 2. 김서방 찾기
>    두 문제다 어렵지 않게 풀었으나 첫번째 문제에서 빈배열을 삽입하는 과정에서 나름 애를 먹었다.. for문으로 넣어줘서 해결하긴 했는데.. 찾아보자.

다음은 어려웠던 중간값 string 비교문제이다

```js
const solution = (string, n) => {
  return string.sort((x, y) => {
    x[n] === y[n] ? x.localCompare(y) : x[n].localeCompare(y[n]);
  });
};
```

## 탑

```js
function solution(heights) {
  let result = [];
  for (let i = heights.length - 1; i >= 0; i--) {
    for (let j = i - 1; j >= 0; j--) {
      if (heights[j] > heights[i]) {
        result.unshift(j + 1);
        j = -1;
      } else if (j === 0) {
        result.unshift(0);
      }
    }
  }
  result.unshift(0);
  return result;
}
```
