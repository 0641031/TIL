### [hackerrank - Permuting Two Arrays](https://www.hackerrank.com/challenges/two-arrays/problem)

Consider two n-element arrays of integers, **A = [A[0], A[1],..., A[n-1]]** and **B = [B[0], B[1],..., B[n-1]]**. You want to permute them into some **A<sup>'</sup>** and **B<sup>'</sup>** such that the relation **A<sup>'</sup>[i] + B<sup>'</sup>[i] >= k** holds for all **i** where **0 <= i < n**. For example, if **A = [0, 1]**, **B = [0, 2]**, and **k = 1**, a valid **A<sup>'</sup>, B<sup>'</sup>** satisfying our relation would be **A<sup>'</sup> = [1, 0]** and **B<sup>'</sup> = [0, 2]**, **1 + 0 >= 1** and **0 + 2 >= 1**.

You are given **q** queries consisting of **A**, **B**, and **k**. For each query, print YES on a new line if some permutation  **A<sup>'</sup>**, **B<sup>'</sup>** satisfying the relation above exists. Otherwise, print NO.


**Function Description**

Complete the twoArrays function in the editor below. It should return a string, either YES or NO.

twoArrays has the following parameter(s):

* k: an integer
* A: an array of integers
* B: an array of integers


**Input Format**

The first line contains an integer **q**, the number of queries.

The next **q** sets of **3** lines are as follows:

* The first line contains two space-separated integers **n** and **k**, the size of both arrays **A** and **B**, and the relation variable.
* The second line contains **n** space-separated integers **A[i]**.
* The third line contains **n** space-separated integers **B[i]**.


**Output Format**

For each query, print YES on a new line if valid permutations exist. Otherwise, print NO.



Example: 
```
Input: 
2
3 10
2 1 3
7 8 9
4 5
1 2 2 1
3 3 3 4

Output: 
YES
NO
```

---

Answer:
```
function twoArrays(k, A, B) {
    // B는 내림차순으로 정렬
    B.sort((a, b) => { return a - b})
    // A는 오름차순으로 정렬하고 every로 조건 확인
    return A.sort((a, b) => { return b - a }).every((el, idx) => {
        return (el + B[idx]) >= k
    }) ? 'YES' : 'NO'
}
```
