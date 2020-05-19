### [hackerrank - Minimum Absolute Difference in an Array](https://www.hackerrank.com/challenges/minimum-absolute-difference-in-an-array/problem)

Consider an array of integers, __arr = [arr[0], arr[1],...,arr[n-1]]__. We define the [absolute difference](https://en.wikipedia.org/wiki/Absolute_difference) between two elements, __a[i]__ and __a[j]__ (where i !== j), to be the absolute value of __a[i] - a[j]__.

Given an array of integers, find and print the minimum absolute difference between any two elements in the array. For example, given the array __arr = [-2, 2, 4]__ we can create __3__ pairs of numbers: __[-2, 2]__,__[-2, 4]__ and __[2, 4]__. The absolute differences for these pairs are __|(-2) - 2| = 4__, __|(-2) - 4| = 6__ and __|2 - 4| = 2__. The minimum absolute difference is __2__.


**Function Description**

Complete the minimumAbsoluteDifference function in the editor below. It should return an integer that represents the minimum absolute difference between any pair of elements.

minimumAbsoluteDifference has the following parameter(s):

* n: an integer that represents the length of arr
* arr: an array of integers

**Input Format**

The first line contains a single integer __n__, the size of __arr__.
The second line contains __n__ space-separated integers __arr[i]__.

**Output Format**

Print the minimum absolute difference between any two elements in the array.


Example: 
```
Input: 
3
3 -7 0

Output: 
3
```

Explanation

The smallest absolute difference is __|3 - 0| = 3__.


---

Answer:
```

function minimumAbsoluteDifference(arr) {
    // 오름차순으로 정렬.
    arr.sort((a, b) => { return a - b })
    let result = Math.abs(arr[0] - arr[1]);
    for(let i=0; i<arr.length-1; i++){
        let temp = Math.abs(arr[i] - arr[i+1]);
        result = result > temp ? temp : result;
    }
    return result
}
```
