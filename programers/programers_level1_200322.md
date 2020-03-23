# programers_level1 

20200319 시작

## sql 알게된 점

1. DISTINCT는 중복을 제거
2. max는 최댓값 구하기, ex) SELECT max(DATETIME), min 동일
3. limit 1 주기
4. count(*)
5. group by 특정 속성을 기준으로 그룹화 하여 검색할 때 그룹화 할 속성을 지정한다.




---

1. H-index


```js
function solution(citations) {
    let hIndex = citations.length;
    while(hIndex>1){
        const more = citations.filter(item=> item>=hInde.length;
        const less = citations.filter(item=> item<=hInde.length;
        if(more>=hIndex&&less<=hIndex){
            return hIndex
        }
        hIndex--
    }
    return 0
}
```

2. 최댓값 구하기 (sql)

```sql
SELECT max(DATETIME) as 시간 from ANIMAL_INS;
```

3. 모든 레코드 조회하기(sql)

```sql
-- 코드를 입력하세요
SELECT * from ANIMAL_INS order by ANIMAL_ID;
```

4. 역순 정렬하기(sql)

```sql
-- 코드를 입력하세요
SELECT NAME, DATETIME from ANIMAL_INS order by ANIMAL_ID desc;
```

5. 아픈 동물찾기(sql)

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME from ANIMAL_INS where INTAKE_CONDITION = "Sick";
```

6. 어린 동물 찾기 (sql)

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME from ANIMAL_INS where INTAKE_CONDITION != "Aged" order by ANIMAL_ID;
```

7. 동물의 아이디와 이름

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME from ANIMAL_INS order by ANIMAL_ID;
```

8. 여러 기준으로 정렬하기

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID, NAME, DATETIME from ANIMAL_INS order by NAME, DATETIME desc;
```

9. 상위 n개 레코드

```sql
-- 코드를 입력하세요
SELECT name from ANIMAL_INS order by DATETIME limit 1;
```

10. 최솟값 구하기

```sql
-- 코드를 입력하세요
SELECT DATETIME as 시간 from ANIMAL_INS order by DATETIME asc limit 1;
```

11. 동물의 수 구하기

```sql
-- 코드를 입력하세요
SELECT count(*) from ANIMAL_INS;
```

12. 중복 제거하기

```sql
-- 코드를 입력하세요
SELECT COUNT(DISTINCT NAME) from ANIMAL_INS;
```

13. 고양이와 개는 몇마리 있을까

```sql
-- 코드를 입력하세요
SELECT DISTINCT ANIMAL_TYPE, COUNT(*) from ANIMAL_INS group by ANIMAL_TYPE;
```

14. 동명 동물 수 찾기

```sql
-- 코드를 입력하세요
SELECT DISTINCT NAME, COUNT(*) as COUNT
from ANIMAL_INS
where NAME is not NULL
group by NAME Having COUNT>=2;
```

15. 이름이 있는 동물 찾기

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID from ANIMAL_INS where NAME is not NULL;
```

16. 이름이 없는 동물 찾기

```sql
-- 코드를 입력하세요
SELECT ANIMAL_ID from ANIMAL_INS where NAME IS NULL order by ANIMAL_ID asc;
```

---

## js

1. p, y 문자열 찾기

```js
function solution(s){
    const pNum = [...s].filter(item=> item==="P"||item==="p").length;
    const yNum = [...s].filter(item=> item==="Y"||item==="y").length;
    return pNum===yNum ? true : false
}
```

2. 문자열 내림차순 정리

```js
function solution(s) {
    const upperText = [...s.replace(/[a-z]/g, "")].sort((x,y)=> y.localeCompare(x))
    const lowerText = [...s.replace(/[A-Z]/g, "")].sort((x,y)=> y.localeCompare(x))
    return lowerText.concat(upperText).join("")
}
```

3. 완주하지 못한 선수

```js
function solution(participant, completion) {
    participant.sort();
    completion.sort();
    for(let i=0; i<participant.length ; i++){
        if(participant[i]!==completion[i]){
            return participant[i]
        }
        completion.splice(i, 1, null)
    }
}
```

4. 모의고사

```js
function solution(answers) {
    let first = [1,2,3,4,5];
    let second = [2,1,2,3,2,4,2,5];
    let third = [3,3,1,1,2,2,4,4,5,5];
    let firstScore =0, secondScore=0, thirdScore=0;
    for(let i=0; i<answers.length; i++){
        let firstI = i%5;
        let secondI = i%8;
        let thirdI = i%10;
        if(answers[i]===first[firstI]){
            firstScore++
        }
        if(answers[i]===second[secondI]){
            secondScore++
        }
        if(answers[i]===third[thirdI]){
            thirdScore++
        }
    }
    
    const scores = [firstScore, secondScore, thirdScore];
    const maxScore = Math.max.apply(null, scores);
    let result = [];
    for(let i=0; i<scores.length; i++){
        if(maxScore===scores[i]){
            result.push(i+1)
        }
    }
    return result
}
```

5. 문자열 다루기 기본

```js
function solution(s) {
    const temp = parseInt(s)
    if (temp==s && s.length === 4 || s.length===6){
        return true
    }else{
        return false
    }
}
function solution2(s) {
    var regex = /^\d{6}$|^\d{4}$/;
  return regex.test(s);
}
```

6. 김서방 찾기

```js
function solution(seoul) {
    const index = seoul.indexOf("Kim")
    return `김서방은 ${index}에 있다`
}
```

7. 수박수박수

```js
function solution(n) {
    const result = "수박".repeat(5000);
    return result.slice(0, n)
}
```

8. 같은 숫자는 싫어

```js
function solution(arr){
    let result = [];
    for(let i=0; i-1<arr.length; i++){
        if(arr[i]!==arr[i+1]){
            result.push(arr[i])
        }
    }
    return result
}
```

9. 가운데 글자 가져오기

```js
function solution(s) {
    const idx = Math.trunc(s.length/2)
    return  s.slice(s.length%2===0 ? idx-1 : idx, idx+1)
}
```

10. 두 정수의 합

```js
function solution(a, b) {
    let result = 0, x, y;
    if(a===b) return a;
    if(a>b){
        x=a;
        y=b
    }else{
        x=b;
        y=a;
    }
    for(let i=y; i<=x; i++){
        result+=i
    }
    return result
}
```

11. 약수의 합

```js
function solution(n) {
    if(!n) return 0;
    let result = 1;
    for(let i=2; i<=n; i++){
        if(n%i===0){
            result+=i
        }
    }
    return result
}
```

12. 나누어 떨어지는 숫자 배열

```js
function solution(arr, divisor) {
    let result = [];
    for(let i=0; i<arr.length; i++){
        if(arr[i]%divisor===0){
            result.push(arr[i])
        }
    }
    if(!result.length) result.push(-1)
    return result.sort((x,y)=> x-y);
}
```

13. 소수 찾기

```js
// 실패
// 함수 분리 성공햇으나 효율성

function solution(n) {
    let result = 0;
    for(let i=2; i<=n; i++){
        const check = primaryNumCheck(i);
        if(check){
            result+=check
        }
    }
    return result
}

const primaryNumCheck = num => {
    let score = 0;
    for(let i=2; i<=num; i++){
        if(num%i===0){
            score++
        }
    }
    if(score===1) return score;
}

// 성공
// 예전 근환이형 코드 가독성이 떨어지나 n수 이하의 소수를 가져올 떄 사용하면 유용할듯

function solution(n) {
  let token = [];
  let answer = [];
  for (let i = 2; i <= n; ++i) {
      console.log(token)
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

14. 자릿수 더하기

```js
function solution(n){
    const target = n.toString().split('');
    let result = 0;
    for(let i=0; i<target.length; i++){
        result += parseInt(target[i])
    }
    return result
}
```

15. 자연수 뒤집어 배열로 만들기

```js
function solution(n) {
    let target = [...n.toString()].reverse();
    for(let i=0; i<target.length; i++){
        target[i] = parseInt(target[i])
    }
    return target
}
```

16. 이상한 숫자 만들기

```js
function solution(s) {
    let target = s.split(" "), result=[];
    for(let i=0; i<target.length; i++){
        for(let j=0; j<target[i].length; j++){
            if(j%2===0){
                result.push(target[i][j].toUpperCase())
            }else{
                result.push(target[i][j].toLowerCase())
            }
        }
        if(i!==target.length-1) result.push(" ");
    }
    return result.join('')
}
```