### [hackerrank - Kangaroo](https://www.hackerrank.com/challenges/kangaroo/problem)

You are choreographing a circus show with various animals. For one act, you are given two kangaroos on a number line ready to jump in the positive direction (i.e, toward positive infinity).

* The first kangaroo starts at location __x1__ and moves at a rate of __v1__ meters per jump.
* The second kangaroo starts at location __x2__ and moves at a rate of __v2__ meters per jump.

You have to figure out a way to get both kangaroos at the same location at the same time as part of the show. If it is possible, return YES, otherwise return NO.

For example, kangaroo 1 starts at x1 = 2 with a jump distance v1 = 1 and kangaroo 2 starts at x2 = 1 with a jump distance of v2 = 2. After one jump, they are both at x = 3, (x1 + v1 = 2 + 1, x2 + v2 = 1 + 2), so our answer is YES.


**Function Description**

Complete the function kangaroo in the editor below. It should return YES if they reach the same position at the same time, or NO if they don't.

kangaroo has the following parameter(s):

* x1, v1: integers, starting position and jump distance for kangaroo 1
* x2, v2: integers, starting position and jump distance for kangaroo 2


**Input Format**

A single line of four space-separated integers denoting the respective values of x1, v1, x2, and v2.


**Constraints**

* 0 <= x1 <= x2 <= 10000
* 1 <= v1 <= 10000
* 1 <= v2 <= 10000


**Output Format**

Print YES if they can land on the same location at the same time; otherwise, print NO.


Example: 
```
Input: 
0 3 4 2

Output: 
YES

Explanation:
The kangaroos meet at the same location (number 12) after same number of jumps (4 jumps).
```

---

Answer:
```
function kangaroo(x1, v1, x2, v2) {
    // 조건에 x1이 x2보다 작은 숫자라고 나와있기 때문에 v1과 v2만 비교하면 됨.
    if(v1 <= v2){
        return 'NO'
    }
    while(x1 < x2){
        x1 += v1;
        x2 += v2;
    }
    // 같은수를 건너뛰고 x1이 x2보다 앞서 나갈 수 있으므로 확인.
    return x1 === x2 ? 'YES' : 'NO'
}
```

<sub>v1과 v2 비교하는데서 등호 빼먹어서 time limit 걸렸었다</sub>
