### [hackerrank - Climbing the Leaderboard](https://www.hackerrank.com/challenges/climbing-the-leaderboard/problem)

Alice is playing an arcade game and wants to climb to the top of the leaderboard and wants to track her ranking. The game uses [Dense Ranking](https://en.wikipedia.org/wiki/Ranking#Dense_ranking_.28.221223.22_ranking.29), so its leaderboard works like this:

* The player with the highest score is ranked number __1__ on the leaderboard.
* Players who have equal scores receive the same ranking number, and the next player(s) receive the immediately following ranking number.
For example, the four players on the leaderboard have high scores of 100, 90, 90, and 80. Those players will have ranks 1, 2, 2, and 3, respectively. If Alice's scores are 70, 80 and 105, her rankings after each game are 4<sup>th</sup>, 3<sup>rd</sup> and 1<sup>st</sup>.


**Function Description**

Complete the climbingLeaderboard function in the editor below. It should return an integer array where each element __res[j]__ represents Alice's rank after the __j<sup>th</sup>__ game.

climbingLeaderboard has the following parameter(s):

* scores: an array of integers that represent leaderboard scores
* alice: an array of integers that represent Alice's scores


**Input Format**

* The first line contains an integer __n__, the number of players on the leaderboard.
* The next line contains __n__ space-separated integers __scores[i]__, the leaderboard scores in decreasing order.
* The next line contains an integer, __m__, denoting the number games Alice plays.
* The last line contains __m__ space-separated integers __alice[j]__, the game scores.


**Output Format**

Print __m__ integers. The __j<sup>th</sup>__ integer should indicate Alice's rank after playing the __j<sup>th</sup>__ game.


Example: 
```
Input: 
scores : [100, 100, 50, 40, 40, 20, 10]
alice: [5, 20, 50, 120]

Output: 
6
4
2
1
```

---

Answer:
```
function climbingLeaderboard(scores, alice) {
    let obj = {};
    let ranking = 1;
    // 중복값 제거를 위해 점수와 랭킹을 담은 객체 만들어서,
    scores.forEach(el => {
        if(!obj[el]){
            obj[el] = ranking;
            ranking += 1;
        } 
    })
    // 점수배열을 만들고 오름차순으로 정렬.
    let rank = Object.keys(obj)
    rank.sort((a, b) => { return a - b })
    let result = [];
    for(let i=0; i<alice.length; i++){
        for(let j=0; j<rank.length; j++){
            if(alice[i] < rank[j]){
                result.push(obj[rank[j]]+1); break;
            }else if(alice[i] == rank[j] || j === rank.length-1){
                result.push(obj[rank[j]]); break;
            }
        }
    }
    return result
}
```

위의 답으로 하면 time limits으로 통과하는 못하는 케이스가 있음. for문을 아래와 같이 수정.

```
for(let i=0; i<alice.length; i++){
    for(let j=start; j<rank.length; j++){
        if(alice[i] < rank[j]){
            result.push(obj[rank[j]]+1); break;
        }else if(alice[i] == rank[j] || j === rank.length-1){
            result.push(obj[rank[j]]); break;
        }else{
            start++;
        }
    }
}
```

오름차순으로 진행되기 때문에 뒤에 나올 alice의 범위가 좁혀지므로 시작하는 index를 증가시켜주면 됨.


###### reference
* [https://ejiaah.com/algorithm/hackerrank/Climbing-the-Leaderboard/](https://ejiaah.com/algorithm/hackerrank/Climbing-the-Leaderboard/)
