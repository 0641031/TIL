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

