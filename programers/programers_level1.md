# programers_level1 

20200319 시작


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