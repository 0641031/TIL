### [Leetcode - Maximum Subarray](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/528/week-1/3285/)

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example: 
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

Answer:
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    let arr = [];
    let sum = 0;
    for(let i=0;i<nums.length;i++){
        // 현재요소까지 더한 값보다 현재요소가 크면 시작 시점을 현재요소로.
        sum = sum+nums[i] < nums[i] ? nums[i] : sum + nums[i]
        // 그렇게 나올 수 있는 모든 경우의 합을 arr 배열에 넣고,
        arr.push(sum)
    }
    // 배열의 최대값을 반환.
    return Math.max(...arr);
};
```

###### reference 
* [Max Contiguous Subarray Sum - Cubic Time To Kadane's Algorithm ("Maximum Subarray" on LeetCode)](https://www.youtube.com/watch?v=2MmGzdiKR9Y)

