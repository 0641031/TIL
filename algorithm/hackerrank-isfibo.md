### [hackerrank - Is Fibo](https://www.hackerrank.com/challenges/is-fibo/problem)

You are given an integer, __N__. Write a program to determine if __N__ is an element of the Fibonacci sequence.

The first few elements of the Fibonacci sequence are __0, 1, 1, 2, 3, 5, 8, 13, ...__. A Fibonacci sequence is one where every element is a sum of the previous two elements in the sequence. The first two elements are __0__ and __1__.



**Input Format**

The first line contains __T__, number of test cases.
__T__ lines follow. Each line contains an integer __N__.


**Output Format**

Display IsFibo if __N__ is a Fibonacci number and IsNotFibo if it is not. The output for each test case should be displayed in a new line.



Example: 
```
Input: 
3
5
7
8

Output: 
IsFibo
IsNotFibo
IsFibo
```

Explanation:

1. 5 is a Fibonacci number given by 2 + 3
2. 7 is not a Fibonacci number
3. 8 is a Fibonacci number given by 5 + 3

---

Answer:
```
function solve(n) {
    let prev = 0, next = 1, sum = 0;
    let isFibo = true;
    while(next < n){
        sum = prev + next;
        prev = next;
        next = sum
    }
    // next가 n과 동일하면 피보나치 숫자, n보다 크면 피보나치 숫자가 아니므로
    isFibo = next === n ? true : false;
    return isFibo ? "IsFibo" : "IsNotFibo"
}
```
