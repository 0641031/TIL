### [hackerrank - Regular Expressions III](https://www.hackerrank.com/challenges/js10-regexp-3/problem)

**Task**

Complete the function in the editor below by returning a RegExp object, _re_, that matches every integer in some string _s_.

**Constraints**

* The length of string is _s_ >= 3.
* It's guaranteed that string _s_ contains at least one integer.

**Output Format**

The function must return a RegExp object that matches every integer in some string _s_.

Example 1: 
```
Input: 102, 1948948 and 1.3 and 4.5
Output: 
102
1948948
1
3
4
5
Explanation: When we call match on string  and pass the correct RegExp as our argument, 
it returns the following array of results: [ '102', '1948948', '1', '3', '4', '5' ].
```
---

Answer:
```
function regexVar() {
    let re = /[0-9]+/g
    return re;
}
```

숫자 외의 문자를 기준으로 나눠주면 된다. [0-9]는 \d 로도 쓸 수 있다. `re = /\d+/g` 도 가능.


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)
* [https://regexr.com/](https://regexr.com/)