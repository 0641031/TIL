### [hackerrank - Two Strings](https://www.hackerrank.com/challenges/two-strings/problem)

WGiven two strings, determine if they share a common substring. A substring may be as small as one character.

For example, the words "a", "and", "art" share the common substring __a__. The words "be" and "cat" do not share a substring.


**Function Description**

Complete the function twoStrings in the editor below. It should return a string, either YES or NO based on whether the strings share a common substring.

twoStrings has the following parameter(s):

* s1, s2: two strings to analyze .

**Input Format**

The first line contains a single integer __p__, the number of test cases.

The following __p__ pairs of lines are as follows:

* The first line contains string __s1__.
* The second line contains string __s2__.

**Output Format**

For each pair of strings, return YES or NO.


Example: 
```
Input: 
2
hello
world
hi
world

Output: 
YES
NO
```

Explanation

1. s1 = "hello", s2 = "world". The substrings **"o"** and **"l"** are common to both strings.
2. a = "hi", s2 = "world". s1 and s2 share no common substrings.


---

Answer:
```
function twoStrings(s1, s2) {
    // filter는 주어진 조건을 통과하는 요소를 모아 새로운 배열을 반환하므로, 
    // 반환 값의 길이로 중복되는 문자가 있는지 확인.
    return s1.split('').filter(el => {
        return s2.includes(el)
    }).length > 0 ? 'YES' : 'NO'
}
```
