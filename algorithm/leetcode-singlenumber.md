### [Leetcode - Single Number](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/528/week-1/3283/)

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example 1:
```
Input: [2,2,1]
Output: 1
```

Example 2:
```
Input: [4,1,2,1,2]
Output: 4
```

Answer:
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    return nums.sort().filter((el,idx,arr)=>{
        return el !== arr[idx-1] && el !== arr[idx+1]
    })
};
```

<sub>예전에 푼 적 있는데, 풀고 비트연산자까지 공부했지만 여전히 활용을 못함...</sub>

[Bitwise operators](https://github.com/0641031/TIL/blob/master/JavaScript/bitwise-operators-01.md)