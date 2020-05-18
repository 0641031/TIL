### [hackerrank - Mark and Toys](https://www.hackerrank.com/challenges/mark-and-toys/problem)

Mark and Jane are very happy after having their first child. Their son loves toys, so Mark wants to buy some. There are a number of different toys lying in front of him, tagged with their prices. Mark has only a certain amount to spend, and he wants to maximize the number of toys he buys with this money.

Given a list of prices and an amount to spend, what is the maximum number of toys Mark can buy? For example, if __prices = [1, 2, 3, 4]__ and Mark has __k = 7__ to spend, he can buy items __[1, 2, 3]__ for __6__, or __[3, 4]__ for __7__ units of currency. He would choose the first group of __3__ items.


**Function Description**

Complete the function maximumToys in the editor below. It should return an integer representing the maximum number of toys Mark can purchase.

maximumToys has the following parameter(s):

* prices: an array of integers representing toy prices
* k: an integer, Mark's budget

**Input Format**

The first line contains two integers, __n__ and __k__, the number of priced toys and the amount Mark has to spend.
The next line contains  __n__ space-separated integers __prices[i]__

**Output Format**

An integer that denotes the maximum number of toys Mark can buy for his son.


Example: 
```
Input: 
7 50
1 12 5 111 200 1000 10

Output: 
4
```

Explanation

He can buy only __4__ toys at most. These toys have the following prices: __1, 2, 5, 10__.


---

Answer:
```
function maximumToys(prices, k) {
    let sum = 0;
    let count = 0;
    // 가격이 싼 순서대로 정렬을 해준 다음,
    prices.sort((a, b) => a - b)
    for(let i=0; i<prices.length; i++){
    	// k값 보다 크기 전까지 더하면서 개수를 세준다.
        if(sum + prices[i] <= k){
            sum += prices[i];
            count += 1;
        }else{
            return count;
        }
    }
}
```
