### Bitwise operators

* [알고리즘 문제](https://leetcode.com/problems/single-number/)풀다가 비트연산자 라는 것을 알게 됨.

#### 비트 연산자는 피연산자를 32개의 비트(0과 1) 집합으로 취급하는 연산자. 2진수로 연산하지만 10진수로 반환함.
 

1. `a & b` : 각각 대응하는 비트가 모두 1이면 1을 반환.
10 - 2진수로 1010
12 - 2진수로 1100
10 & 12 는 1000이 되므로 8을 반환한다.

2. `a | b` : 각각 대응하는 비트가 모두 1이거나 한 쪽이 1이면 1을 반환.
10 | 12 는 1110이므로 14를 반환.

3. `a ^ b` : 대응하는 비트가 서로 같으면 0, 다르면 1을 반환. 
10 ^ 12 는 0110 이므로 6을 반환.

4. `~a` : 대응하는 비트의 반대 값을 반환한다.
이 부분에서 32비트 부호 연산에 대하여 전혀 몰라서 한참 헤맸다.

[2진수의 음수표현법에 대한 글](https://namsieon.com/entry/%EA%B8%B0%EB%B3%B8%EC%9B%90%EB%A6%AC-2%EC%A7%84%EC%88%98%EC%9D%98-%EC%9D%8C%EC%88%98%ED%91%9C%ED%98%84%EB%B2%95)

[구글링해서 봐도 이해가 잘 안되다가 보고 이마를 탁 치게 한 글](https://code.i-harness.com/ko-kr/q/c1320)

더해서 0이 되는 수를 만들기 위해 A-A가 아니라 A+(-A) 하는 것을 알면 이해에 도움이 된다. 



#### 비트연산자 응용 방법


* [다중 선택값을 저장하고 사용해야 할 경우](https://cyberx.tistory.com/51)

* ~~가 Math.floor()와 같은 역할을 한다고 하지만 숫자가 커지거나, 음수에는 바르게 작동하지 않는다. [참고](https://stackoverflow.com/questions/13847053/difference-between-and-math-floor) 


* [16진수 값을 파싱하여 RGB 색상 값을 얻을 때](https://codeday.me/ko/qa/20190320/52455.html)


<sub>bitwise shift operator까지 학습하고 읽어봐야 할 [포스팅](https://velog.io/@jakeseo_me/2019-04-30-1604-%EC%9E%91%EC%84%B1%EB%90%A8-7qjv3gv9ad)</sub>




###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators)








