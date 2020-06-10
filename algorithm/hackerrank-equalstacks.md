### [hackerrank - Equal Stacks](https://www.hackerrank.com/challenges/equal-stacks/problem)

You have three stacks of cylinders where each cylinder has the same diameter, but they may vary in height. You can change the height of a stack by removing and discarding its topmost cylinder any number of times.

Find the maximum possible height of the stacks such that all of the stacks are exactly the same height. This means you must remove zero or more cylinders from the top of zero or more of the three stacks until they're all the same height, then print the height. The removals must be performed in such a way as to maximize the height.

Note: An empty stack is still a stack.


**Input Format**

The first line contains three space-separated integers, **n1**, **n2**, and **n3**, describing the respective number of cylinders in stacks **1**, **2**, and **3**. The subsequent lines describe the respective heights of each cylinder in a stack from top to bottom:

* The second line contains **n1** space-separated integers describing the cylinder heights in stack **1**. The first element is the top of the stack.
* The third line contains **n2** space-separated integers describing the cylinder heights in stack **2**. The first element is the top of the stack.
* The fourth line contains **n3** space-separated integers describing the cylinder heights in stack **3**. The first element is the top of the stack.


**Output Format**

Print a single integer denoting the maximum height at which all stacks will be of equal height.


Example: 
```
Input: 
5 3 4
3 2 1 1 1
4 3 2
1 1 4 1

Output: 
5
```

Explanation:

![image1](https://s3.amazonaws.com/hr-challenge-images/21404/1465645257-57311b88de-piles1.png)

![image2](https://s3.amazonaws.com/hr-challenge-images/21404/1465645312-e48f85c176-piles2.png)

1. 8 - 3 = 5
2. 9 - 4 = 5
3. 7 - 1 - 1 = 5

All three stacks now have **height = 5**. Thus, we print **5** as our answer

---

Answer:
```
function equalStacks(h1, h2, h3) {
    let sum1 = h1.reduce((acc, cur) => { return acc += cur });
    let sum2 = h2.reduce((acc, cur) => { return acc += cur });
    let sum3 = h3.reduce((acc, cur) => { return acc += cur });
    // 최소값을 기준으로 높이를 맟춤.
    let min = Math.min(sum1, sum2, sum3);
    while(!(sum1 === sum2 && sum1 === sum3)){
        if(sum1 > min){
            sum1 -= h1.shift();
        }
        if(sum2 > min){
            sum2 -= h2.shift();
        }
        if(sum3 > min){
            sum3 -= h3.shift();
        }
        min = Math.min(sum1, sum2, sum3)
    }
    // while문의 조건이 sum1, sum2, sum3이 같을 때 이므로
    return sum1
}
```

* Array.prototype.shift() : 원본 배열의 첫번째 요소를 제거하고, 제거된 요소를 반환함.
* Array.prototype.pop() : 원본 배열의 마지막 요소를 제거하고, 제거된 요소를 반환함.


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

