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

```js
function solution(priorities, location) {
  const targetNum = priorities[location];
  let answerKey = location + 1;
  let count = 1;
  while (1) {
    if (priorities[0] === Math.max.apply(Math, priorities)) {
      if (answerKey === 1) {
        return count;
      } else {
        priorities.shift();
        count++;
      }
    } else {
      priorities.push(priorities.shift());
    }
    answerKey > 1 ? answerKey-- : (answerKey = priorities.length);
  }
}
```

# 다리를 지나는 트럭

```js
function solution(bridge_length, weight, truck_weights) {
  var answer = 0;
  let total_truck_weight = 0;
  let bridge_queue = [],
    weight_queue = [];
  do {
    // 다리를 건너는 트럭 이동
    for (let i in bridge_queue) {
      bridge_queue[i]--;
    }
    if (bridge_queue[0] == 0) {
      total_truck_weight -= weight_queue.shift();
      bridge_queue.shift();
    }
    // 다리가 견딜 수 있으면 트럭 1개 올리기
    if (total_truck_weight + truck_weights[0] <= weight) {
      weight_queue.push(truck_weights[0]);
      bridge_queue.push(bridge_length);
      total_truck_weight += truck_weights.shift();
    }
    answer++;
  } while (bridge_queue.length > 0);
  return answer;
}
// truck_weight(대기트럭)을 passing_bridge에 추가해줌
// bridge_length초가 무조건 걸리는데 1초를 다른 트럭과 공유하는 가 안하는 가가 주요 point
// 지나가고 잇는 시간이 bridge의 길이를 통과했을 때 shift() 해주기
// truck_weights와 passing_bridege가 비웟다면
```

# 기능개발

```js
// 실패한 케이스 3시간 품
function solution(progresses, speeds) {
  //  queue 개념으로 접근해보자
  let result = [];
  let queue = [];
  for (let i = 0; i < progresses.length; i++) {
    let deployDay = 0;
    while (progresses[i] < 100) {
      progresses[i] += speeds[i];
      deployDay++;
    }
    queue.push(deployDay);
  }
  let primaryArr = [];
  let count = 1;
  for (let i = 1; i < queue.length; i++) {
    primaryArr.push(queue[i - 1]);
    let primaryNum = Math.max.apply(null, primaryArr);
    // 현재 숫자가 primaryNum보다 크면 현재 count 들어가고 아니면 count추가
    if (queue[i] > primaryNum) {
      result.push(count);
      count = 1;
      if (i === queue.length - 1) {
        result.push(count);
      }
    } else {
      count++;
    }
  }
  return result;
}
```
