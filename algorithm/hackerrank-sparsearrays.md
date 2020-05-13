### [hackerrank - Sparse Arrays](https://www.hackerrank.com/challenges/sparse-arrays/problem)

There is a collection of input strings and a collection of query strings. For each query string, determine how many times it occurs in the list of input strings.

For example, given input __strings = ['ab', 'ab', 'abc']__ and __queries = ['ab', 'abc', 'bc']__, we find 2 instances of 'ab', 1 of 'abc' and 0 of 'bc'. For each query, we add an element to our return array, __result = [2, 1, 0]__.

**Function Description**

Complete the function matchingStrings in the editor below. The function must return an array of integers representing the frequency of occurrence of each query string in strings.

matchingStrings has the following parameters:

* strings - an array of strings to search
* queries - an array of query strings

---

Answer:
```
function matchingStrings(strings, queries) {
    return queries.reduce((acc, cur, idx) => {
        let count = 0;
        strings.forEach(el => {
            if(el === cur){
            	// 같은 요소일 경우를 센 다음,
                count += 1
            }
        })
        // 누적배열에 넣어줌.
        acc.push(count)
        return acc
    },[])
}
```

filter를 사용 할 수도 있다.

```
function matchingStrings(strings, queries) {
    let result = [];
    queries.forEach(el => {
    	// 조건에 맞는 배열의 길이를 result에 추가
        result.push(strings.filter(cur => el === cur).length)
    })
    return result
}
```
