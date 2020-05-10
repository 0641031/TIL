### [hackerrank - Game of Thrones - I](https://www.hackerrank.com/challenges/game-of-thrones/problem)

Dothraki are planning an attack to usurp King Robert's throne. King Robert learns of this conspiracy from Raven and plans to lock the single door through which the enemy can enter his kingdom.

But, to lock the door he needs a key that is an anagram of a palindrome. He starts to go through his box of strings, checking to see if they can be rearranged into a palindrome.

For example, given the string __s = [aabbccdd]__, one way it can be arranged into a palindrome is __abcddcba__.


**Function Description**

Complete the gameOfThrones function below to determine whether a given string can be rearranged into a palindrome. If it is possible, return **YES**, otherwise return **NO**.

gameOfThrones has the following parameter(s):

* s: a string to analyze


**Input Format**

A single line which contains __s__, the input string.


**Output Format**

A single line which contains YES or NO.


Example 1: 
```
Input: 
aaabbbb

Output: 
YES

Explanation:
A palindromic permutation of the given string is bbaaabb.
```

Example 2: 
```
Input: 
cdefghmnopqrstuvw

Output: 
NO

Explanation:
Palindromes longer than 1 character are made up of pairs of characters. There are none here.
```

---

Answer:
```
function gameOfThrones(s) {
    let obj = {};
    // 각 문자의 개수를 객체에 담고,
    s.split('').forEach(el => {
        obj[el] ? obj[el] += 1 : obj[el] = 1;
    })
    // 문자열의 길이가 짝수인지 홀수인지 확인.
    let even = s.length % 2 === 0;
    let count = 0;
    Object.values(obj).forEach(el => {
        // 문자열의 개수가 홀수인 경우를 계산.
        if(el % 2 !== 0) { count += 1 };
    })
    let result = even ? count === 0 : count === 1;
    return result ? 'YES' : 'NO'
}
```
