### [Leetcode - Happy Number](https://leetcode.com/problems/happy-number/)

Write an algorithm to determine if a number n is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Return True if n is a happy number, and False if not.

Example: 
```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

Answer:
```
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {

    let result = n;
    // 숫자를 제곱하여 더한 결과값을 넣을 배열.
    let sum = [];

    while(result !== 1){
        let arr = result.toString().split('');
        result = arr.reduce((acc,cur) => {
            return acc + (parseInt(cur) * parseInt(cur)) 
        },0)
		
		// 결과값이 이미 배열에 있다면 같은 계산이 반복되는 것이므로 false 반환.
        if(sum.indexOf(result)!== -1){
            return false;
        }else{
            sum.push(result);
        }
    }
    return true;
};
```


