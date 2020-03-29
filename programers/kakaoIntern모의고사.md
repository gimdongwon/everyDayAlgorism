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

5. 징검다리

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