### [Leetcode - Group Anagrams](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/528/week-1/3288/)

Given an array of strings, group anagrams together.

Example 1: 
```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

Note:

1. All inputs will be in lowercase.
2. The order of your output does not matter.


split으로 문자열을 배열로 만든다음에 sort로 정렬하여 비교.

Answer:
```
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
    let obj = {};
    strs.forEach((el) => {
        let temp = el.split('').sort();
        // 이미 동일한 문자열이 있으면 새로운 배열을 만들고, 아니면 기존 배열에 추가.
        obj[temp] ? obj[temp].push(el) : obj[temp] = [el]
    })
    return Object.values(obj)
};
```
split을 사용하지 않고, [...string]을 사용할 수도 있음.

###### reference
* [https://medium.com/javascript-in-plain-english/algorithms-101-group-anagrams-in-javascript-b3e3c10d211e](https://medium.com/javascript-in-plain-english/algorithms-101-group-anagrams-in-javascript-b3e3c10d211e)