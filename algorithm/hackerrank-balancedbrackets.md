### [hackerrank - Balanced Brackets](https://www.hackerrank.com/challenges/balanced-brackets/problem)

A bracket is considered to be any one of the following characters: (, ), {, }, [, or ].

Two brackets are considered to be a matched pair if the an opening bracket (i.e., (, [, or {) occurs to the left of a closing bracket (i.e., ), ], or }) of the exact same type. There are three types of matched pairs of brackets: [], {}, and ().

A matching pair of brackets is not balanced if the set of brackets it encloses are not matched. For example, {[(])} is not balanced because the contents in between { and } are not balanced. The pair of square brackets encloses a single, unbalanced opening bracket, (, and the pair of parentheses encloses a single, unbalanced closing square bracket, ].

By this logic, we say a sequence of brackets is balanced if the following conditions are met:

* It contains no unmatched brackets.
* The subset of brackets enclosed within the confines of a matched pair of brackets is also a matched pair of brackets.

Given **n** strings of brackets, determine whether each sequence of brackets is balanced. If a string is balanced, return YES. Otherwise, return NO.


**Function Description**

Complete the function isBalanced in the editor below. It must return a string: YES if the sequence is balanced or NO if it is not.

isBalanced has the following parameter(s):

* s: a string of brackets


**Input Format**

* The first line contains a single integer **n**, the number of strings.
* Each of the next **n** lines contains a single string **s**, a sequence of brackets.


**Output Format**

For each string, return YES or NO.


Example: 
```
Input: 
3
{[()]}
{[(])}
{{[[(())]]}}

Output: 
YES
NO
YES
```

Explanation

1. The string {[()]} meets both criteria for being a balanced string, so we print YES on a new line.
2. The string {[(])} is not balanced because the brackets enclosed by the matched pair { and } are not balanced: [(]).
3. The string {{[[(())]]}} meets both criteria for being a balanced string, so we print YES on a new line.


---

Answer:
```
function isBalanced(s) {
    let brackets = { '(': ')', '[': ']', '{': '}' };
    let result = [];
    for(let i=0; i < s.length; i++) {
        // 여는 괄호가 나오면 그에 해당하는 닫는 괄호를 result배열에 담고
        if (Object.keys(brackets).includes(s[i])) {
            result.push(brackets[s[i]])
        } else {
            // 여는 괄호가 아닌 경우, 가장 나중에 들어간 닫는 괄호와 일치하는지 확인
            // .pop() : 배열의 가장 마지막 요소를 제거하고 그 값은 반환함
            if(s[i] !== result.pop()){
                return 'NO'
            }
        }
    }
    // 모든 괄호가 다 닫혔는지 확인
    if(result.length > 0) {
        return 'NO'
    }
    return 'YES'
}
```
