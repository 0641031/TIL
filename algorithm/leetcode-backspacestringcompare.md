### [Leetcode - Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)

Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

Example 1: 
```
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

Example 2: 
```
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

Note:

* 1 <= S.length <= 200
* 1 <= T.length <= 200
* S and T only contain lowercase letters and '#' characters.


Answer:
```
/**
 * @param {string} S
 * @param {string} T
 * @return {boolean}
 */
var backspaceCompare = function(S, T) {
    const getResult = (str) => {
        let arr = [...str]
        return arr.reduce((acc,cur,idx) => {
            // 현재 값이 '#'이면 누적값(배열) 맨 뒤의 요소를 삭제하고, 아니면 누적값에 추가
            cur === '#' ? acc.pop() : acc.push(cur)
            return acc
        }, []).join('')
    }
    return getResult(S) === getResult(T)
};
```
