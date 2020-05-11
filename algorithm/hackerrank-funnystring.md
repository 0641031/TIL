### [hackerrank - Funny String](https://www.hackerrank.com/challenges/funny-string/problem)

In this challenge, you will determine whether a string is funny or not. To determine whether a string is funny, create a copy of the string in reverse e.g. __abc → cba__. Iterating through each string, compare the absolute difference in the ascii values of the characters at positions 0 and 1, 1 and 2 and so on to the end. If the list of absolute differences is the same for both strings, they are funny.

Determine whether a give string is funny. If it is, return Funny, otherwise return Not Funny.

For example, given the string __s = lmnop__, the ordinal values of the charcters are __[108, 109, 110, 111, 112]__. __s reverse = ponml__ and the ordinals are __[112, 111, 110, 109, 108]__. The absolute differences of the adjacent elements for both strings are __[1, 1, 1, 1]__, so the answer is Funny.

**Function Description**

Complete the funnyString function in the editor below. For each test case, it should return a string, either Funny or Not Funny.

funnyString has the following parameter(s):

* s: a string to test


**Input Format**

The first line contains an integer __q__, the number of queries.

The next __q__ lines each contain a string, __s__.


**Output Format**

For each string __s__ print whether it is Funny or Not Funny on a new line.


Example 1: 
```
Input: 
2
acxz

Output: 
Funny

Explanation:
s = acxz, r = zxca, 
Corresponding ASCII values of characters of the strings:
s = [97, 99, 120, 122] and r = [122, 120, 99, 97]
For both the strings the adjacent difference list is [2, 21, 2] so we print Funny.
```

---

Answer:
```
function funnyString(s) {
    let arr = s.split('');
    let result1 = [];
    let result2 = [];
    for(let i = 0; i<arr.length-1; i++){
        result1.push(Math.abs(arr[i].charCodeAt() - arr[i+1].charCodeAt()))
        result2.push(Math.abs(arr[arr.length-i-1].charCodeAt() - arr[arr.length-i-2].charCodeAt()))
    }
    return result1.join('') === result2.join('') ? 'Funny' : 'Not Funny'
}
```
각각 배열에 담아서 결과값을 비교했는데,

```
function funnyString(s) {
    let arr = s.split('');
    for(let i = 0; i<arr.length-1; i++){
        if (Math.abs(arr[i].charCodeAt() - arr[i+1].charCodeAt()) 
            !==  Math.abs(arr[arr.length-i-1].charCodeAt() - arr[arr.length-i-2].charCodeAt())){
            return 'Not Funny'
        }
    }
    return 'Funny';
}
```

정방향으로 진행하는 배열의 차이와 역방향으로 진행하는 배열의 차이가 다를 때, 바로 'Not Funny'를 반환하면 됨.
