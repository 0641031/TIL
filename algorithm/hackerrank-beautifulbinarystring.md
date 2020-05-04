### [hackerrank - Beautiful Binary String](https://www.hackerrank.com/challenges/beautiful-binary-string/problem)

Alice has a binary string. She thinks a binary string is beautiful if and only if it doesn't contain the substring "010".

In one step, Alice can change a 0 to a 1 or vice versa. Count and print the minimum number of steps needed to make Alice see the string as beautiful.

For example, if Alice's string is b=010 she can change any one element and have a beautiful string.

**Function Description**

Complete the beautifulBinaryString function in the editor below. It should return an integer representing the minimum moves required.

beautifulBinaryString has the following parameter(s):

* b: a string of binary digits

**Input Format**

The first line contains an integer n, the length of binary string.
The second line contains a single binary string b.

**Output Format**

Print the minimum number of steps needed to make the string beautiful.


Example 1: 
```
Input: 0101010
Output: 2 
```

Example 2: 
```
Input: 01100
Output: 0
Explanation: The substring "010" does not occur in b, so the string is already beautiful and we print 0. 
```
---

Answer:
```
function beautifulBinaryString(b) {
    let count = b.match(/010/g);
    return count === null? 0 : count.length
}
```

##### String.prototype.match()

match() 문자열이 정규식과 매치되는 부분을 검색. 정규식과 일치하는 문자열을 **배열**로 반환하고, 일치하는 문자열이 없으면 **null**을 반환. 
매개변수를 전달하지 않으면 빈 배열을 반환.



###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match)