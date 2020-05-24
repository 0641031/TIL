### [hackerrank - Picking Numbers](https://www.hackerrank.com/challenges/picking-numbers/problem)

Given an array of integers, find and print the maximum number of integers you can select from the array such that the absolute difference between any two of the chosen integers is less than or equal to __1__. For example, if your array is __a = [1, 1, 2, 2, 4, 4, 5, 5, 5]__, you can create two subarrays meeting the criterion: __[1, 1, 2, 2]__ and __[4, 4, 5, 5, 5]__. The maximum length subarray has __5__ elements.


**Function Description**

Complete the pickingNumbers function in the editor below. It should return an integer that represents the length of the longest array that can be created.

pickingNumbers has the following parameter(s):

* a: an array of integers


**Input Format**

The first line contains a single integer __n__, the size of the array __a__.
The second line contains __n__ space-separated integers __a[i]__.

**Constraints**

* 2 <= n <= 100
* 0 < a[i] < 100
* The answer will be >= 2

**Output Format**

A single integer denoting the maximum number of integers you can choose from the array such that the absolute difference between any two of the chosen integers is __<= 1__.


Example: 
```
Input: 
6
4 6 5 3 3 1

Output: 
3
```

Explanation

We choose the following multiset of integers from the array: __{4, 3, 3}__. Each pair in the multiset has an absolute difference __<= 1__

---

Answer:
```
function pickingNumbers(a) {
    let obj = {};
    for(let i=1; i<100; i++){
        obj[i] = 0;
    }
    a.forEach(el => {
        obj[el] += 1
    })
    let max = 0;
    for(let i=1; i<100; i++){
        if(obj[i] + obj[i+1] > max){
            max = obj[i] + obj[i+1]
        }
    }
    return max
}
```

처음에 실패했던 코드는,

```
function pickingNumbers(a) {
    let obj = {};
    // 배열을 정렬하여 숫자 : 개수를 넣은 객체를 만들고,
    a.sort().forEach(el => {
        obj[el] ? obj[el] += 1 : obj[el] = 1;
    })
    // 숫자로 된 배열을 만들어서
    let arr = Object.keys(obj);
    // 배열의 길이가 1이면 개수를 바로 반납.
    if(arr.length === 1){
        return Object.values(obj)[0]
    }
    let prev = 0;
    let diff = false;
    for(let i=0; i<arr.length-1; i++){
        // 그 앞뒤 숫자의 차이가 1이고, 개수의 합을 비교했는데,
        if((arr[i+1] - arr[i] === 1) && obj[arr[i]] + obj[arr[i+1]] > prev){
            prev = obj[arr[i]] + obj[arr[i+1]]
        }
    }
    return prev
}
```

이건 두 개수의 합보다 하나의 개수가 더 클 수 있기 때문에 안됨. 그렇기 때문에 100까지 숫자와 0을 넣은 객체를 만들고 비교를 해야한다.


###### reference
* [https://dev.to/ryhenness/lets-solve-code-challenge---picking-numbers-a32](https://dev.to/ryhenness/lets-solve-code-challenge---picking-numbers-a32)
