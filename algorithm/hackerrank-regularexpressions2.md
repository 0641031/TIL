### [hackerrank - Regular Expressions II](https://www.hackerrank.com/challenges/js10-regexp-2/problem)

**Task**

Complete the function in the editor below by returning a RegExp object, _re_, that matches any string _s_ satisfying both of the following conditions:

* String _s_ starts with the prefix Mr., Mrs., Ms., Dr., or Er.
* The remainder of string _s_ (i.e., the rest of the string after the prefix) consists of one or more upper and/or lowercase English alphabetic letters (i.e., [a-z] and [A-Z]).

**Constraints**

* The length of string is _s_ >= 3.

**Output Format**

The function must return a RegExp object that matches any string _s_ satisfying both of the given conditions.

Example 1: 
```
Input: Mrs.Y
Output: true
Explanation: This string starts with Mrs., followed by an English alphabetic letter (Y).
```

Example 2: 
```
Input: Er .Abc
Output: false
Explanation: This string starts with Er but there is a space before the period (.), making the string invalid.
```
---

Answer:
```
function regexVar() {
    // Mr, Mrs, Ms, Dr, Er 중 하나로 시작하고
    // .이 오고,
    // 알파벳이 여러번 나오다가 끝남.
    let re = /^(Mr|Mrs|Ms|Dr|Er)\.[A-Za-z]+$/

    return re;
}
```
(Mr|Mrs|Ms|Dr|Er) : [MDE][rs]s? 로 쓸수도 있다. 

[A-Za-z] : [A-z]로 써도 통과는 되지만, [ASCII테이블](http://www.asciitable.com/) A-z사이에는 다른 특수문자도 포함되어 있음.



###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)
* [https://regexr.com/](https://regexr.com/)
* [https://stackoverflow.com/questions/4923380/difference-between-regex-a-z-and-a-za-z](https://stackoverflow.com/questions/4923380/difference-between-regex-a-z-and-a-za-z)