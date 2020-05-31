### [hackerrank - Halloween party](https://www.hackerrank.com/challenges/halloween-party/problem)

Alex is attending a Halloween party with his girlfriend, Silvia. At the party, Silvia spots the corner of an infinite chocolate bar (two dimensional, infinitely long in width and length).

If the chocolate can be served only as 1 x 1 sized pieces and Alex can cut the chocolate bar exactly __K__ times, what is the maximum number of chocolate pieces Alex can cut and give Silvia?



**Input Format**

The first line contains an integer __T__, the number of test cases. __T__ lines follow.
Each line contains an integer __K__.


**Output Format**

__T__ lines; each line should contain an integer that denotes the maximum number of pieces that can be obtained for each test case.


Example: 
```
Input: 
4
5
6
7
8

Output: 
6
9
12
16
```

더해서 input이 나오는 숫자 중, 곱해서 나오는 가장 큰 수 구하기

---

Answer:
```
function halloweenParty(k) {
    return Math.floor(k/2) * (k - Math.floor(k/2))
}
```

* Math.floor() : 소수점 이하를 버린 정수를 반환.

* Math.ceil() : 소수점 이하를 올린 정수 반환.


위의 답은 `Math.floor(k/2) * Math.ceil(k/2)`도 된다.

참고로 

* Math.round() : 소수점 이하를 반올림한 정수 반환.


##### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/floor](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil)
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/round](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math/round)