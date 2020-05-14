### [hackerrank - Ice Cream Parlor](https://www.hackerrank.com/challenges/icecream-parlor/problem)

Sunny and Johnny like to pool their money and go to the ice cream parlor. Johnny never buys the same flavor that Sunny does. The only other rule they have is that they spend all of their money.

Given a list of prices for the flavors of ice cream, select the two that will cost all of the money they have.

For example, they have __m = 6__ to spend and there are flavors costing __cost = [1, 3, 4, 5, 6]__. The two flavors costing 1 and 5 meet the criteria. Using 1-based indexing, they are at indices 1 and 4.

**Function Description**

Complete the icecreamParlor function in the editor below. It should return an array containing the indices of the prices of the two flavors they buy, sorted ascending.

icecreamParlor has the following parameter(s):

* m: an integer denoting the amount of money they have to spend
* cost: an integer array denoting the cost of each flavor of ice cream

Example: 
```
Input: 
5
1 4 5 3 2

Output: 
1 4

Explanation:
The first time, they pool together m = 4 dollars. 
Of the five flavors available that day, flavors 1 and 4 have a total cost of 1 + 3 = 4.
```

---

Answer:
```
function icecreamParlor(m, arr) {
    for(let i=0; i<arr.length; i++){
        for(let j=i+1; j<arr.length; j++){
            if((arr[i] + arr[j]) === m){
                return [i+1, j+1];
            }
        }
    }
}
```

map을 이용하면 한 번의 반복문으로 결과 도출이 가능함.

```
function icecreamParlor(m, arr) {
    let map = new Map();
    for(let i=0; i<arr.length; i++){
        let value = m - arr[i];
        if(map.has(value)){
            return [map.get(value)+1, i+1];
        }
        map.set(arr[i], i)
    }
}
```

<sub>반환하는 배열의 순서는 상관 없으니 위의 반복문에서 i가 작은 숫자 일 때 답을 도출하지 않아도 되는데 꼭 순서대로 해야한다는 생각에 사로잡히는 것 같다. </sub>
