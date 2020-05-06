### [hackerrank - The Love-Letter Mystery](https://www.hackerrank.com/challenges/the-love-letter-mystery/problem)

James found a love letter that his friend Harry has written to his girlfriend. James is a prankster, so he decides to meddle with the letter. He changes all the words in the letter into [palindromes](https://en.wikipedia.org/wiki/Palindrome).

To do this, he follows two rules:

1. He can only reduce the value of a letter by 1, i.e. he can change d to c, but he cannot change c to d or d to b.
2. The letter a may not be reduced any further.

Each reduction in the value of any letter is counted as a single operation. Find the minimum number of operations required to convert a given string into a palindrome.

For example, given the string __s = cde__, the following two operations are performed: cd**e** → cd**d** → cdc.

**Function Description**

Complete the theLoveLetterMystery function in the editor below. It should return the integer representing the minimum number of operations needed to make the string a palindrome.

theLoveLetterMystery has the following parameter(s):

* s: a string

**Input Format**

The first line contains an integer __q__, the number of queries.

The next __q__ lines will each contain a string __s__.

**Output Format**

A single line containing the minimum number of operations corresponding to each test case.


Example: 
```
Input: 
4
abc
abcba
abcd
cba

Output: 
2
0
4
2 
```

Explanation

1. For the first test case, ab**c** → ab**b** → aba.
2. For the second test case, abcba is already a palindromic string.
3. For the third test case, abc**d** → abc**c** → abc**b** → ab**c**a → abba.
4. For the fourth test case, **c**ba → **b**ba → aba.

---

Answer:
```
function theLoveLetterMystery(s) {
    let arr = s.split('');
    let result = 0;
    // 중간값까지 반복문을 돌려서 대응하는 요소와 UTF-16코드 차이를 계산.
    for(let i = 0; i < arr.length/2; i++){
        result += Math.abs(arr[i].charCodeAt() - arr[arr.length-i-1].charCodeAt())
    }
    return result;
}
```

##### String.prototype.charCodeAt()

주어진 인덱스에 대한 UTF-16 코드를 나타내는 0부터 65535 사이의 정수를 반환. 범위 밖으로 넘어갔을 경우에 NaN을 반환.

'abc'.charCodeAt()을 하면 a에 해당하는 코드를 반환함.


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)
