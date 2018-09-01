# programers 한번에 못푼것들

## 최소공배수, 최대공약수

```js
function gcdlcm(a, b) {
    var answer = [];
    const max_num = Math.max(a,b);
    const min_num = Math.min(a,b);
    let gcdCandi = [];
    
    for (let i=1;i<=max_num;i++){
        if(max_num%i===0&& min_num%i===0&min_num===i){
            answer.push(i);
        }
        else if(max_num%i===0&&min_num%i===0){
            gcdCandi.push(i);
        }
        answer[0] = gcdCandi.pop();
    }
    answer[1] = (min_num * max_num) / answer[0];
    return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(gcdlcm(3,12));
```

## 문자열 다루기

alpha_string46함수는 문자열 s를 매개변수로 입력받습니다.
s의 길이가 4혹은 6이고, 숫자로만 구성되있는지 확인해주는 함수를 완성하세요.
예를들어 s가 a234이면 False를 리턴하고 1234라면 True를 리턴하면 됩니다

```js
실패코드 ㅠㅠ
function alpha_string46(s){
  var result = true;
  if(s.length === 4 || s.length === 6){
      return s.split('').every(item=>parseInt(item)== Number );
  }else(
  return false;
  );
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log( alpha_string46("a234") );
```

>나는 이문제가 왜이리 어렵지 계속 풀어보자

## 예산(2018 summer 코딩)

다 못품

```js
function solution(d, budget) {
    let newArray = d.sort();
    let result =0;
    for(let i=0; i<newArray.length; i++){
        result += newArray[i]
        if(result===budget){
            return i+1
        }else if(result > budget){
            return i
        }
    }
}
```