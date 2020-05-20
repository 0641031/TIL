### [hackerrank - Grid Challenge](https://www.hackerrank.com/challenges/grid-challenge/problem)

Given a square grid of characters in the range ascii[a-z], rearrange elements of each row alphabetically, ascending. Determine if the columns are also in ascending alphabetical order, top to bottom. Return YES if they are or NO if they are not.

For example, given:
```
a b c
a d e
e f g
```
The rows are already in alphabetical order. The columns a a e, b d f and c e g are also in alphabetical order, so the answer would be YES. Only elements within the same row can be rearranged. They cannot be moved to a different row.


**Function Description**

Complete the gridChallenge function in the editor below. It should return a string, either YES or NO.

gridChallenge has the following parameter(s):

* grid: an array of strings

**Input Format**

The first line contains __t__, the number of testcases.

Each of the next __t__ sets of lines are described as follows:

- The first line contains __n__, the number of rows and columns in the grid.
- The next __n__ lines contains a string of length __n__

**Output Format**

For each test case, on a separate line print YES if it is possible to rearrange the grid alphabetically ascending in both its rows and columns, or NO otherwise.


Example: 
```
Input: 
1
5
ebacd
fghij
olmkn
trpqs
xywuv

Output: 
YES
```

Explanation

The 5 x 5 grid in the 1 test case can be reordered to
```
abcde
fghij
klmno
pqrst
uvwxy
```


---

Answer:
```
function gridChallenge(grid) {
    // 각 문자열을 배열에 담고
    let arr = grid.map(el => {
        return el.split('').sort();
    })
    for(let i=0; i<arr[0].length; i++){
        for(let j=0; j<arr.length-1; j++){
            // utf-16코드로 비교함.
            if(arr[j][i].charCodeAt() > arr[j+1][i].charCodeAt()){
                return 'NO'
            }   
        }
    }
    return 'YES'
}
```
