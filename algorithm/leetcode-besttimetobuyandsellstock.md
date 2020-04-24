### [Leetcode - Best Time to Buy and Sell Stock II](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/528/week-1/3287/)

Say you have an array prices for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

Example 1: 
```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

Example 2: 
```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

Answer:
```
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let prev = prices[0];
    let sum = 0;
    for(let i=1; i<prices.length; i++){
        if(prices[i] > prev){
            sum += prices[i] - prev;
        }
        prev = prices[i]
        
    }
    return sum
};
```

reduce 사용하면,
```
var maxProfit = function(prices) {
    return prices.reduce((acc, cur, i, arr) => {
        return cur < arr[i+1] ? acc + (arr[i+1] - cur) : acc
    }, 0)
};
```
