### [hackerrank - Priyanka and Toys](https://www.hackerrank.com/challenges/priyanka-and-toys/problem)

Priyanka works for an international toy company that ships by container. Her task is to the determine the lowest cost way to combine her orders for shipping. She has a list of item weights. The shipping company has a requirement that all items loaded in a container must weigh less than or equal to 4 units plus the weight of the minimum weight item. All items meeting that requirement will be shipped in one container.

What is the smallest number of containers that can be contracted to ship the items based on the given list of weights?

For example, there are items with weights **w = [1, 2, 3, 4, 5, 10, 11, 12, 13]**. This can be broken into two containers: **[1, 2, 3, 4, 5]** and **[10, 11, 12, 13]**. Each container will contain items weighing within **4** units of the minimum weight item.


**Function Description**

Complete the toys function in the editor below. It should return the minimum number of containers required to ship.

toys has the following parameter(s):

* w: an array of integers that represent the weights of each order to ship


**Input Format**

* The first line contains an integer **n**, the number of orders to ship.
* The next line contains **n** space-separated integers, **w[1], w[2],..., w[n]**, representing the orders in a weight array.


**Output Format**

Return the integer value of the number of containers Priyanka must contract to ship all of the toys.



Example: 
```
Input: 
8
1 2 3 21 7 12 14 21

Output: 
4
```

1. The first container holds items weighing 1, 2 and 3. (weights in range 1...5)
2. The second container holds the items weighing 21 units. (21...25)
3. The third container holds the item weighing 7 units. (7...11)
4. The fourth container holds the items weighing 12 and 14 units. (12...14)

 **4** containers are required.


---

Answer:
```
function toys(w) {
    // 오름차순으로 정렬
    w.sort((a, b) => { return a - b })
    // unit이 시작되는 값을 배열의 첫번째 값으로 하고,
    let start = w[0];
    return w.reduce((acc, cur) => {
    	// unit의 범위를 넘으면, unit의 시작값을 갱신하고, container(=누적값) + 1 해줌.
        if(cur > start + 4){
            start = cur;
            acc += 1
        }
        return acc
    }, 1)
    // 첫번째 컨테이너를 세고 시작해야하기 때문에 1로 시작값 설정.
}

```
