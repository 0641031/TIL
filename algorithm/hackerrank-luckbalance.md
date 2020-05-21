### [hackerrank - Luck Balance](https://www.hackerrank.com/challenges/luck-balance/problem)

Lena is preparing for an important coding competition that is preceded by a number of sequential preliminary contests. Initially, her luck balance is 0. She believes in "saving luck", and wants to check her theory. Each contest is described by two integers, __L[i]__ and __T[i]__:

* __L[i]__ is the amount of luck associated with a contest. If Lena wins the contest, her luck balance will decrease by __L[i]__; if she loses it, her luck balance will increase by __L[i]__.
* __T[i]__ denotes the contest's importance rating. It's equal to __1__ if the contest is important, and it's equal to __0__ if it's unimportant. If Lena loses no more than __k__ important contests, what is the maximum amount of luck she can have after competing in all the preliminary contests? This value may be negative.


**Function Description**

Complete the luckBalance function in the editor below. It should return an integer that represents the maximum luck balance achievable.

luckBalance has the following parameter(s):

* k: the number of important contests Lena can lose
* contests: a 2D array of integers where each __contests[i]__ contains two integers that represent the luck balance and importance of the __i<sup>th</sup>__ contest.


**Input Format**

The first line contains two space-separated integers __n__ and __k__, the number of preliminary contests and the maximum number of important contests Lena can lose.

Each of the next __n__ lines contains two space-separated integers, __L[i]__ and __T[i]__, the contest's luck balance and its importance rating.

**Output Format**

Print a single integer denoting the maximum amount of luck Lena can have after all the contests.


Example: 
```
Input: 
6 3
5 1
2 1
1 1
8 1
10 0
5 0

Output: 
29
```

Explanation

There are __6__ contests. Of these contests, __4__ are important and she cannot lose more than __k = 3__ of them. Lena maximizes her luck if she wins the __3<sup>rd</sup>__ important contest (where __L[i] = 1__) and loses all of the other five contests for a total luck balance of __5 + 2 + 8 + 10 + 5 - 1 = 29__.

---

Answer:
```
function luckBalance(k, contests) {
    // luck의 숫자를 기준으로 내림차순 정렬
    contests.sort((a, b) => b[0] - a[0]);
    let luck = 0;
    contests.forEach(el => {
        // not important하기 때문에 무조건 더함.
        if(el[1] === 0) {
            luck += el[0];
        // important의 경우 k만큼 luck을 가져올 수 있기 때문에, luck을 더하면서 k-1해줌.
        }else if(k > 0 && el[1] === 1){
            luck += el[0];
            k -= 1
        // 이기는 important게임의 luck을 마이너스
        }else{
            luck -= el[0]
        }
    })
    return luck
}
```

k가 중요한 대회에서 질 수 있는 최대의 수이므로 최대한의 luck을 가져가기 위해서 큰 luck을 먼저 k만큼 더함.
