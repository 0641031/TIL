### [hackerrank - Service Lane](https://www.hackerrank.com/challenges/service-lane/problem)

Calvin is driving his favorite vehicle on the 101 freeway. He notices that the check engine light of his vehicle is on, and he wants to service it immediately to avoid any risks. Luckily, a service lane runs parallel to the highway. The service lane varies in width along its length.

![service lane](https://hr-testcases.s3.amazonaws.com/1331)

You will be given an array of widths at points along the road (indices), then a list of the indices of entry and exit points. Considering each entry and exit point pair, calculate the maximum size vehicle that can travel that segment of the service lane safely.

For example, there are __n = 4__ measurements yielding __width = [2, 3, 2, 1]__. If our entry index, __i = 1__ and our exit, __j = 2__, there are two segment widths of __2__ and __3__ respectively. The widest vehicle that can fit through both is __2__. If __i = 2__ and __j = 4__, our widths are __[3, 2, 1]__ which limits vehicle width to __1__.



Example: 
```
Input: 
8 5
2 3 1 2 3 2 3 3
0 3
4 6
6 7
3 5
0 7

Output: 
1
2
3
2
1
```

코드 완성하는 부분에서 넓이 배열을 매개변수로 전달하지 않기 때문에, 거기서부터 수정해야한다. 문제는 최소넓이를 구하는 것.

---

Answer:
```
function serviceLane(cases, width) {
    return cases.reduce((acc, cur) => {
        // slice가 배열을 변형하지 않음. splice쓰면 안됨.
        let min = Math.min(...width.slice(cur[0], cur[1]+1));
        acc.push(min)
        return acc
    }, [])
}
```
