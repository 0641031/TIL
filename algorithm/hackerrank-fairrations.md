### [hackerrank - Fair Rations](https://www.hackerrank.com/challenges/fair-rations/problem)

You are the benevolent ruler of Rankhacker Castle, and today you're distributing bread. Your subjects are in a line, and some of them already have some loaves. Times are hard and your castle's food stocks are dwindling, so you must distribute as few loaves as possible according to the following rules:

1. Every time you give a loaf of bread to some person **i**, you must also give a loaf of bread to the person immediately in front of or behind them in the line (i.e., persons **i+1** or **i-1**).
2. After all the bread is distributed, each person must have an even number of loaves.

Given the number of loaves already held by each citizen, find and print the minimum number of loaves you must distribute to satisfy the two rules above. If this is not possible, print NO.

For example, the people in line have loaves **B = [4, 5, 6, 7]**. We can first give a loaf to **i = 3** and **i = 4** so **B = [4, 5, 7, 8]**. Next we give a loaf to  and  and have  which satisfies our conditions. We had to distribute  loaves.


**Function Description**

Complete the fairRations function in the editor below. It should return an integer that represents the minimum number of loaves required.

fairRations has the following parameter(s):

* B: an array of integers that represent the number of loaves each persons starts with .


**Input Format**

* The first line contains an integer **N**, the number of subjects in the bread line.
* The second line contains **N** space-separated integers **B[i]**.


**Output Format**

Print a single integer taht denotes the minimum number of loaves that must be distributed so that every person has an even number of loaves. If it's not possible to do this, print NO.

Example: 
```
Input: 
5
2 3 4 5 6

Output: 
4
```

Explanation:

The initial distribution is **(2, 3, 4, 5, 6)**. The requirements can be met as follows:

1. Give **1** loaf of bread each to the second and third people so that the distribution becomes **(2, 4, 5, 5, 6)**.
2. Give **1** loaf of bread each to the third and fourth people so that the distribution becomes **(2, 4, 6, 6, 6)**.


Each of the **N** subjects has an even number of loaves after **4** loaves were distributed.

---

Answer:

```
function fairRations(B) {
    let result = 0;
    B.forEach((el, idx) => {
        if(el % 2 === 1){
            B[idx] += 1;
            B[idx+1] += 1;
            result += 2;
        }
    })
    // 배열이 모두 짝수인지 확인
    return B.every(el => el % 2 === 0) ? result : 'NO'
}
```