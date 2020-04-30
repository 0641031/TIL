### [Leetcode - Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)

We have a collection of stones, each stone has a positive integer weight.

Each turn, we choose the two **heaviest** stones and smash them together.  Suppose the stones have weights x and y with x <= y.  The result of this smash is:

* If x == y, both stones are totally destroyed;
* If x != y, the stone of weight x is totally destroyed, and the stone of weight y has new weight y-x.

At the end, there is at most 1 stone left.  Return the weight of this stone (or 0 if there are no stones left.)


Example 1: 
```
Input: [2,7,4,1,8,1]
Output: 1
Explanation: 
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of last stone.
```

Answer:
```
/**
 * @param {number[]} stones
 * @return {number}
 */
var lastStoneWeight = function(stones) {
    // 배열의 길이가 1과 같거나 작아질 때까지 반복.
    while(stones.length > 1){
        let i = stones.length - 1;
        // 배열을 오름차순으로 정렬
        stones.sort((a,b) => { return a-b });
        // 두개의 크기가 같으면 둘 다 없어지기 때문에 배열에서 삭제
        if(stones[i] == stones[i-1]){
            stones.splice(i-1, 2);
        }else{
            let temp = stones[i] - stones[i-1];
            stones.splice(i-1, 2);
            // 두개의 차이를 배열에 추가
            stones.push(temp);
        }
    }
    return stones
};
```

어차피 가장 큰 두 숫자는 배열에서 삭제해야되기 때문에, 삭제될 값을 변수에 할당하여 활용할 수도 있다.

```
var lastStoneWeight = function(stones) {
    while(stones.length > 1){
        stones.sort((a,b) => { return a-b })
        // 배열의 가장 마지막 요소를 가져옴.
        let bigger = stones.pop();
        let smaller = stones.pop();
        if(bigger !== smaller){
            stones.push(bigger-smaller)
        }
    }
    return stones
};
```
