### Leetcode - Counting Elements

Given an integer array arr, count element x such that x + 1 is also in arr.

If there're duplicates in arr, count them seperately.


Example 1: 
```
Input: arr = [1,2,3]
Output: 2
Explanation: 1 and 2 are counted cause 2 and 3 are in arr.
```

Example 2: 
```
Input: arr = [1,1,3,3,5,5,7,7]
Output: 0
Explanation: No numbers are counted, cause there's no 2, 4, 6, or 8 in arr.
```

Answer:
```
/**
 * @param {number[]} arr
 * @return {number}
 */
var countElements = function(arr) {
    return arr.reduce((acc,cur,idx)=>{
        // 현재값 더하기 1이 배열 안에 있는지 확인
        return arr.indexOf(cur+1) !== -1 ? acc+=1 : acc
    },0)
    
};
```
