### [hackerrank - Chocolate Feast](https://www.hackerrank.com/challenges/chocolate-feast/problem)

Little Bobby loves chocolate. He frequently goes to his favorite __5 & 10__ store, Penny Auntie, to buy them. They are having a promotion at Penny Auntie. If Bobby saves enough wrappers, he can turn them in for a free chocolate.

For example, Bobby has __n = 15__ to spend on bars of chocolate that cost __c = 3__ each. He can turn in __m = 2__ wrappers to receive another bar. Initially, he buys __5__ bars and has __5__ wrappers after eating them. He turns in __4__ of them, leaving him with __1__, for __2__ more bars. After eating those two, he has __3__ wrappers, turns in __2__ leaving him with __1__ wrapper and his new bar. Once he eats that one, he has __2__ wrappers and turns them in for another bar. After eating that one, he only has __1__ wrapper, and his feast ends. Overall, he has eaten __5 + 2 + 1 + 1 = 9__ bars.


**Function Description**

Complete the chocolateFeast function in the editor below. It must return the number of chocolates Bobby can eat after taking full advantage of the promotion.

chocolateFeast has the following parameter(s):

* n: an integer representing Bobby's initial amount of money
* c: an integer representing the cost of a chocolate bar
* m: an integer representing the number of wrappers he can turn in for a free bar

Note: Little Bobby will always turn in his wrappers if he has enough to get a free chocolate.


**Input Format**

The first line contains an integer, __t__, denoting the number of test cases to analyze.
Each of the next __t__ lines contains three space-separated integers: __n__, __c__, and __m__. They represent money to spend, cost of a chocolate, and the number of wrappers he can turn in for a free chocolate.


**Output Format**

For each trip to Penny Auntie, print the total number of chocolates Bobby eats on a new line.


Example: 
```
Input: 
2
10 2 5
6 2 2

Output: 
6
5
```

Explanation:

1. He spends his 10 dollars on 5 chocolates at 2 dollars apiece. He then eats them and exchanges all 5 wrappers to get 1 more. He eats  chocolates.

2. He spends 6 dollars on 3 chocolates at 2 dollars apiece. He then exchanges 2 of the 3 wrappers for 1 additional piece. Next, he uses his third leftover chocolate wrapper from his initial purchase with the wrapper from his trade-in to do a second trade-in for 1 more piece. At this point he has 1 wrapper left, which is not enough to perform another trade-in. He eats 5 chocolates.

---

Answer:
```
function chocolateFeast(n, c, m) {
    let choco = Math.floor(n/c);
    let bonusChoco = Math.floor(choco/m);
    let restChoco = choco%m;
    let sum = restChoco + bonusChoco
    if(sum >= m){
        bonusChoco += Math.floor(sum/m);
    }
    return choco + bonusChoco
}
```

위 답은 한 케이스에서 계속 실패하는데, 추가로 얻은 초코렛의 개수에 따라 계속해서 초코렛을 교환할 수 있는 경우가 있기 때문에, if문이 아니라 while문으로 써야함. wrapper를 변수로 쓸 생각을 못했다...

```
function chocolateFeast(n, c, m) {
    let choco = Math.floor(n/c);
    let wrapper = choco;

    while(wrapper >= m) {
        let bonusChoco = Math.floor(wrapper/m);
        wrapper = bonusChoco + wrapper % m;
        choco += bonusChoco;
    }
    
    return choco
}
```

<sub>:weary:</sub>
