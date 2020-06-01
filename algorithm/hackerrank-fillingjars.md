### [hackerrank - Filling Jars](https://www.hackerrank.com/challenges/filling-jars/problem)

Animesh has __N__ empty candy jars, numbered from __1__ to __N__, with infinite capacity. He performs __M__ operations. Each operation is described by __3__ integers, __a__, __b__, and __k__. Here, __a__ and __b__ are indices of the jars, and __k__ is the number of candies to be added inside each jar whose index lies between __a__ and __b__ (both inclusive). Can you tell the average number of candies after __M__ operations?



**Input Format**

The first line contains two integers, __N__ and __M__, separated by a single space.

 __M__ lines follow; each of them contains three integers, __a__, __b__, and __k__, separated by spaces.


**Output Format**

A single line containing the average number of candies across __N__ jars, rounded down to the nearest integer.

**Note**: Rounded down means finding the greatest integer which is less than or equal to the given number. E.g. 13.65 and 13.23 are rounded down to 13, while 12.98 is rounded down to 12.




Example: 
```
Input: 
5 3
1 2 100
2 5 100
3 4 100

Output: 
160
```

1. [0 0 0 0 0]
2. [100 100 0 0 0]
3. [100 200 100 100 100]

이 배열의 평균 값을 구하면 됨.

---

Answer:
```
function solve(n, operations) {
    return Math.floor(operations.reduce((acc, cur) => {
        return acc += cur[2] * (cur[1] - cur[0] + 1)
    }, 0) / n)
}
```

결국 전체의 합이 필요하므로 배열을 만들지 않고 합만 구하면 됨.