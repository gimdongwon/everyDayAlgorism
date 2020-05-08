# 카카오 인턴 모의고사

1. 
```js
function solution(board, moves) {
    let transformBoard = [], container=[], result=0;
    for(let i=0; i<board.length; i++){
        transformBoard.push([]);
    }
    // board를 새로로 변형
    for(let i=0; i<board.length; i++){
        for(let j=0; j<board[i].length; j++){
            if(board[i][j]!==0){
                transformBoard[j].push(board[i][j])
            }
        }
    }
    
    for(let i=0; i<moves.length; i++){    
        const currentDoll = transformBoard[moves[i]-1].shift();
        if(currentDoll!==undefined){
         container.unshift(currentDoll)   
        }
        if(container.length>1&&container[0]===container[1]){
            container.shift()
            container.shift()
            result +=2
        }
    }
    return result
}
```

2. 튜플

```js
const solution = (s)=> {
    const sets = s
        .slice(2, s.length-2)
        .split("},{")
        .map(el=> el.split(","))
        .sort((x,y)=>x.length-y.length)
    let result = [...sets[0]]
    for(let i=1; i<sets.length; i++){
        for (const r of result){
            sets[i] = sets[i].filter(set => set!==r)
        }
        result.push(...sets[i])
    }
    return result.map(item=> parseInt(item))
}
```

3. 카카오 이모티콘

```js
function solution(user_id, banned_id) {
    // banned_id에서 같은 값이 유일한 경우 1번
    let starIndex = [], result=1;
    for(let i=0; i<banned_id.length; i++){
        starIndex.push([])
    }
    // banned_id의 *의 index 구하기
    for(let i=0; i<banned_id.length; i++){
        for(let j=0; j<banned_id[i].length; j++){
            if(banned_id[i][j]==="*"){
                starIndex[i].push(j)
            }
        }
    }
    
    // user_id 치환하기
    let newUser_id;
    for(let i=0; i<starIndex.length; i++){
        newUser_id = user_id
        for(let j=0; j<starIndex[i].length; j++){
            newUser_id = newUser_id.map(item=> {
                return item.slice(0, starIndex[i][j]) + "*" + item.slice(starIndex[i][j]+1, item.length)
            });
            
        }
        result*=newUser_id.filter(item=> item===banned_id[i]).length
    }
    return result
    // banned_id에서 같은 값이 두개이상인 경우 2,3번
    
}
```

4. 스노우 타운

```js
function solution(k, room_number) {
    let room = [], usedRoom = [];
    for(let i=1; i<=k; i++){
        room.push(i)
    }
    for(let i=0; i<room_number.length; i++){
        if(!usedRoom.includes(room_number[i])){
            usedRoom.push(room_number[i])
        }else{
            let roomCheck = true, num=room_number[i];
            while(roomCheck){
                num++
                if(!usedRoom.includes(num)){
                    roomCheck = false;
                    usedRoom.push(num)
                }
            }
        }
    }
    return usedRoom
}
```

효율성 탈락.

정답.

```js
const find_empty_room = (x, rooms) =>{
    if(!rooms.get(x)){
        rooms.set(x, x+1);
        return x
    }
    let p = find_empty_room(rooms.get(x), rooms);
    rooms.set(x, p+1);
    return p
}

const solution = (x, room_number) => {
    let rooms = new Map(), answer=[];
    for(let i=0; i<room_number.length; i++){
        let empty_room = find_empty_room(room_number[i], rooms);
        answer.push(empty_room)
    }
    return answer
}
```

1. 징검다리

```js
function solution(stones, k) {
    let result = 1, check = true;
    const checkFn = stonesStr => stonesStr.join("").includes("0".repeat(k));
    let newStones = stones;
    
    while(check){
        newStones = newStones.map(item=> {
            if(item>0){
                return item-1
            }else{
                return item
            }
        })
        if(checkFn(newStones)){
            return result
        }else{
            result++
        }
    }
}
```

## 2020 문자열 압축

```js
function solution(s) {
    let result = [], target=[];
    for(let i=1; i<s.length/2+1; i++){
        let j=0, k=i, strArr=[];
        while(j<s.length){
            strArr.push(s.slice(j, k))
            j+=i
            k+=i
        }
        // console.log(strArr)
        let currentLeng=1, newArr=[];
        for(let p=0; p<strArr.length-1; p++){
            if(strArr[p]===strArr[p+1]){
                currentLeng++
            }else{
                if(currentLeng===1){
                    newArr.push(strArr[p])
                }else{
                    newArr.push(currentLeng)
                    newArr.push(strArr[p])
                    currentLeng = 1;
                }
            }
            if(p===strArr.length-2){
                if(currentLeng!==1) newArr.push(currentLeng);
                // newArr.push(strArr[p])
                newArr.push(strArr[p+1])
            }
        }
        result.push(newArr.join("").length)
    }
    return Math.min.apply(null, result)
}
```