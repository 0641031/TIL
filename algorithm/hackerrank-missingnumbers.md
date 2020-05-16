### [hackerrank - Missing Numbers](https://www.hackerrank.com/challenges/missing-numbers/problem)

Numeros the Artist had two lists that were permutations of one another. He was very proud. Unfortunately, while transporting them from one exhibition to another, some numbers were lost out of the first list. Can you find the missing numbers?

As an example, the array with some numbers missing, __arr = [7, 2, 5, 3, 5, 3]__ . The original array of numbers __brr = [7, 2, 5, 4, 6, 3, 5, 3]__. The numbers missing are __[4, 6]__.

**Function Description**

Complete the missingNumbers function in the editor below. It should return a sorted array of missing numbers.

missingNumbers has the following parameter(s):

* arr: the array with missing numbers
* brr: the original array of numbers

Example: 
```
Input: 
10
203 204 205 206 207 208 203 204 205 206
13
203 204 204 205 206 207 205 208 203 206 205 206 204

Output: 
204 205 206

Explanation:
204 is present in both arrays. Its frequency in arr is 2, while its frequency in brr is 3. 
Similarly, 205 and 206 occur twice in arr, but three times in brr. 
The rest of the numbers have the same frequencies in both lists.
```

---

Answer:
```
function missingNumbers(arr, brr) {    
    let obj = {};
    arr.forEach(el => {
        obj[el] ? obj[el][0] += 1 : obj[el] = [1,0]; 
    })
    brr.forEach(el => {
        obj[el] ? obj[el][1] += 1 : obj[el] = [0,1]; 
    })
    return Object.keys(obj).reduce((acc,cur) => {
        if(obj[cur][0] !== obj[cur][1]){
            acc.push(cur)
        }
        return acc
    }, []).sort((a,b) => { return a-b })
}
```
