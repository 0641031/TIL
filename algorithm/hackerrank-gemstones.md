### [hackerrank - Gemstones](https://www.hackerrank.com/challenges/gem-stones/problem)

John has collected various rocks. Each rock has various minerals embeded in it. Each type of mineral is designated by a lowercase letter in the range __ascii[a-z]__. There may be multiple occurrences of a mineral in a rock. A mineral is called a gemstone if it occurs at least once in each of the rocks in John's collection.

Given a list of minerals embedded in each of John's rocks, display the number of types of gemstones he has in his collection.

For example, the array of mineral composition strings __arr=[abc, abc, bc]__. The minerals __b__ and __c__ appear in each composite, so there are __2__ gemstones.


**Function Description**

Complete the gemstones function in the editor below. It should return an integer representing the number of gemstones found in the list of rocks.

gemstones has the following parameter(s):

* arr: an array of strings

**Input Format**

The first line consists of an integer __n__, the size of __arr__.
Each of the next __n__ lines contains a string __arr[i]__ where each letter represents an occurence of a mineral in the current rock.

**Output Format**

Print the number of types of gemstones in John's collection. If there are none, print __0__.


Example: 
```
Input: 
3
abcdde
baccd
eeabg

Output: 
2
```

Explanation

Only __a__ and __b__ are gemstones because they are the only types that occur in every rock.

---

Answer:
```
function gemstones(arr) {
	// 중복된 문자열 제거
    arr = arr.map(el => {
        let temp = el.split('')
        for(let i=0; i<temp.length; i++){
            if(temp.indexOf(temp[i])!== i){
                temp.splice(i,1);
                i--;
            } 
        }
        return temp.join('')
    })
    let obj = {};
    // 각 문자들이 몇 번 들어갔는지 확인
    arr.forEach(el => {
        el.split('').forEach( cur => {
            obj[cur] ? obj[cur] += 1 : obj[cur] = 1;
        })
    }) 
    // 주어진 배열의 개수만큼 들어간 문자 확인
    return Object.values(obj).reduce((acc,cur) => {
        return cur === arr.length ? acc += 1 : acc
    },0)
}
```


문제에서 ascii[a-z]라는 범위를 지정해주었으므로, 

```
function gemstones(arr) {
    let start = 'a'.charCodeAt();
    let end = 'z'.charCodeAt();
    let count = 0;
    for(let i=start; i<=end; i++){
    	// arr의 모든 요소가 해당 코드의 문자열을 포함하고 있는지 확인
        if(arr.every(el => el.includes(String.fromCharCode(i)))){
            count += 1
        }
    }
    return count
}
```

##### String.fromCharCode()

UTF-16 코드 유닛의 시퀀스로부터 문자열을 생성해 반환.

String.fromCharCode(65, 66, 67);  // "ABC"를 반환


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

