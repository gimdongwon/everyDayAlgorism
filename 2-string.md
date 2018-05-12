### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```
```js
function insensitiveEqual(arr1, arr2){
  return arr1.toUpperCase() === arr2.toUpperCase();
}
```
### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:

```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```

```js
function leftPad (str, num){
  if(str.length < num){
   return str.padStart(num);
  } else{
    return str;
  }
}
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.
```js
function countVowel(str) {
  let count = 0;
  for (let i = 0; i < str.length; i++) {
    if (
      str[i].includes('a') || 
      str[i].includes('e') || 
      str[i].includes('i') || 
      str[i].includes('o') || 
      str[i].includes('u')
    ) {
      count++;
    }
  }
  return count;
}
```

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```
```js
function countChar(str){
  const obj = {};
  for(let i =0; i<str.length; i++){
    const char = str[i];
    //만약 속성이 없다면 
    if(obj[char] == null){ //null check
      obj[char]=1;
    }else{
      obj[char]++;
    }
    //속성값에 1 저장
  }
  return obj;
} 
```
### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)
```js
function reaverseRead(str){
  for(i=0; i < str.length; i++){
  if (str[i]!==str[str.length-i-1]){
    return false;
  }
  return true;
}
}
```
### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```js
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

```js
function slice(str){
  const arr = [];
  for(let i=0; i< str.length; i++){
    for(let j=i+1; j<str.length+1; j++){
    arr.push(str.slice(i,j));}
}
return arr;
}
```
### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```js
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```
```js
내답

function removeDuplicates(str){
  let newStr ='';
  for(let i =0; i< str.length; i++){
    if(!newStr.includes(Str[i])){
      return newStr += str[i];
    }
}return newStr;
}
```

### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.
```js
function secureEmail(email){
  let atPos;
  for(let i=0; i<email.length;i++){
    if (email[i]==='@'){
      atPos=i;
      break;
    }
  }
  const afterAt = email.slice(atPos,email.length);
  const stars = '*'.repeat(atpos);
  return stars + afterAt;
}
// 가정한게 맞는지 검정하라
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.
```js
function swapCase(str){
  let newStr = '';
  for(let i=0; i<str.length; i++){
    if(str[i].toLowerCase()===str[i]){
      newStr += str[i].toUpperCase();
    }else{
      newStr += str[i].toLowerCase();
    }
  }
  return newStr;
}
```
swapCase('JavaScript');
### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```js
내답

function firstConvert(str){
  let newStr;
  for(let i=0; i<str.length; i++){
  if(i===0 || str[i-1]===' '){
  newStr += str[i].toUpperCase();
  }
  else{newStr += str[i];}
}}
```

### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

```javascript

function maxLength(str){
  let maxLen=0;
  let currentLen=0;
  for(let i=0; i < str.length; i++){
    if(str[i]===' '){
      maxLen = maxLen > currentLen ? maxLen : currentLen;
      currentLen = 0;
    }else{
      return currentLen++;
    }
  }
  return maxLen > currentLen ? maxLen : currentLen;
}

function maxLength(str){
  const words = str.split(' ');
  let maxLen=0;
  for(let i=0; i<words.length; i++){
    maxLen = words[i].length > maxLen? words[i].length : maxLen;
  }
  return maxLen;
}
```

### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.

```js
 function snConvert (str, n){
   let newChar= '';
   for(i =0; i<n; i++){
     newChar += str[i];
   }return newChar;
 }
 ```

 ```js
 승하 강사님풀이 (내꺼 에러남 ㅠ)
  function snConvert (str, n){
   let newChar= '';
   for(i =0; i<n && i < str.length; i++){
     newChar += str[i];
   }return newChar;
 }
  ```

```js
강사님풀이 filter
function firstStr(s,n){
  return Array
  .from(s)
  .filter((item, index) => index < n)
  .join('');
}
```

### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.
만약  str[i]===toUpperCase 이면
 i를 가져와서 toDownCase 하고 앞에 다가 '_'를 삽입

```js

//만약  str[i]===toUpperCase 이면
// i를 가져와서 toDownCase 하고 앞에 다가 '_'를 삽입

 function snakeConvert (str){
   let newChar='';
   for(i=0; i < str.length; i++){
   if(str[i].toUpperCase()===str[i] && i !== 0){
     newChar += '_' + str[i].toLowerCase();
   }else{
     newChar += str[i];
   }
   }
   return newChar;
 }
 ```

### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

```js
function snakeConvert (str){
   let newChar='';
   for(i=0; i < str.length; i++){
   if(str[i]=='_'){
    newChar += str[i+1].toUpperCase();
    i++;
   }
   else{
     newChar += str[i];
   }
   }
   return newChar;
 }

 ```
### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

```js
function split (str,separater){
  let arr = [];
  for(i=0; i < str.length; i++){
    if(str[i]==separater){
      arr.push(str.slice(0,i));
      arr.push(str.slice(i+1,str.length));
    }
  }return arr;
}
```
### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

```js
function binaryConvert (str){
  newStr = str.split('');
  let result=0;
  for(i=0, l=newStr.length;l-i>0; i++){
    result += newStr[i] * Math.pow(2,l-i-2);
  }
  return result;
}
```
```js
강사님풀이
for(let i = 0; i<str.length; i++){
  if(str[str.length - i - 1]==='1'){
    result += 2 ** i;
  }
  
}return result;
```
### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
