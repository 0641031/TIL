### [Leetcode - Move Zeroes](https://leetcode.com/problems/move-zeroes/)

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example: 
```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

Note:

1. You must do this in-place without making a copy of the array.
2. Minimize the total number of operations.

Answer:
```
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    for(let i=0;i<nums.length;i++){
        if(nums[i] === 0 && i !== nums.length-1){
            nums.splice(i,1)
            nums.push(0)
            i -= 1
        }
    }
    return nums
};
```

이렇게 제출해도 통과는 됐는데, 뒤에서부터 0을 채우는 거기 때문에 for loop의 시작을 0으로 하지 않고, 배열의 길이로 하면

```
var moveZeroes = function(nums) {
    for(let i=nums.length;i>=0;i--){
        if(nums[i]===0){
            nums.splice(i,1)
            nums.push(0)
        }
    }
    return nums
};
```

그런데, 힌트가 있었다.

:bulb: A two-pointer approach could be helpful here. The idea would be to have one pointer for iterating the array and another pointer that just works on the non-zero elements of the array.

0의 개수만큼 배열의 마지막에 추가하면 되기 때문에,

```
var moveZeroes = function(nums) {
    let count = 0;
    for(let i=0;i < nums.length;i++){
        if(nums[i] !== 0){
            // 순서대로 원본 배열에 0이 아닌 값을 넣어주고,
            nums[count] = nums[i];
            count += 1
        }
    }
    // 뒤에 0을 채워줌.
    for(let i=count;i<nums.length; i++){
        nums[i] = 0;
    }
    return nums
};
```


