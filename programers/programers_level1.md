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