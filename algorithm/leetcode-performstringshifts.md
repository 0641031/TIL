### [Leetcode - Backspace String Compare](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3299/)

You are given a string s containing lowercase English letters, and a matrix shift, where shift[i] = [direction, amount]:

* direction can be 0 (for left shift) or 1 (for right shift). 
* amount is the amount by which string s is to be shifted.
* A left shift by 1 means remove the first character of s and append it to the end.
* Similarly, a right shift by 1 means remove the last character of s and add it to the beginning.

Return the final string after all operations.

Example 1: 
```
Input: s = "abc", shift = [[0,1],[1,2]]
Output: "cab"
Explanation: 
[0,1] means shift to left by 1. "abc" -> "bca"
[1,2] means shift to right by 2. "bca" -> "cab"
```

Answer:
```
/**
 * @param {string} s
 * @param {number[][]} shift
 * @return {string}
 */
var stringShift = function(s, shift) {
    let arr = [...s]
    for(let i=0; i<shift.length; i++){
        let direction = shift[i][0]
        let num = shift[i][1]
        for(let j=0; j<num; j++){
            if(direction === 1){
                // 배열의 마지막 요소를 맨 앞으로 옮김
                arr.unshift(arr.pop())
            }else{
                // 배열의 첫번째 요소를 맨 뒤로 옮김
                arr.push(arr.shift())
            }
        }
    }
    return arr.join('')
};
```

하나씩 숫자를 옮기는 작업을 이동해야하는 숫자만큼 반복하거나,


```
var stringShift = function(s, shift) {
    let arr = [...s]
    for(let i=0; i<shift.length; i++){
        let direction = shift[i][0]
        // 제시된 숫자가 배열의 길이보다 클 수 있기 때문에
        let num =  shift[i][1] % arr.length
        // right
        if(direction === 1){
            let temp = arr.splice(arr.length-num);
            arr.unshift(...temp)
        }else{
            let temp =  arr.splice(0,num);
            arr.push(...temp)
        }
    }
    return arr.join('')
};
```

splice를 이용하여 배열의 요소를 한꺼번에 옮길 수도 있다.

splice에 대한 건 정리한 적이 있는데, 반환값이 헷갈린다... [https://github.com/0641031/TIL/blob/master/JavaScript/array-02.md](https://github.com/0641031/TIL/blob/master/JavaScript/array-02.md)


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
