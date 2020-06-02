### [hackerrank - Drawing Book](https://www.hackerrank.com/challenges/drawing-book/problem)

Brie’s Drawing teacher asks her class to open their books to a page number. Brie can either start turning pages from the front of the book or from the back of the book. She always turns pages one at a time. When she opens the book, page  is always on the right side:

![1](https://s3.amazonaws.com/hr-challenge-images/0/1481920803-d2b54f38f0-book.png)

When she flips page 1, she sees pages 2 and 3. Each page except the last page will always be printed on both sides. The last page may only be printed on the front, given the length of the book. If the book is n pages long, and she wants to turn to page p, what is the minimum number of pages she will turn? She can start at the beginning or the end of the book.

Given n and p, find and print the minimum number of pages Brie must turn in order to arrive at page p.


**Function Description**

Complete the pageCount function in the editor below. It should return the minimum number of pages Brie must turn.

pageCount has the following parameter(s):

* n: the number of pages in the book
* p: the page number to turn to


**Input Format**

* The first line contains an integer n, the number of pages in the book.
* The second line contains an integer, p, the page that Brie's teacher wants her to turn to.


**Output Format**

Print an integer denoting the minimum number of pages Brie must turn to get to page p.



Example: 
```
Input: 
5
4

Output: 
0
```

Explanation:

If Brie starts turning from page 5, she doesn't need to turn any pages:

![2](https://s3.amazonaws.com/hr-challenge-images/22564/1467398392-5d9ac72e45-UntitledDiagram5.png)

Because we want to print the minimum number of page turns, we print 0 as our answer.

---

Answer:
```
function pageCount(n, p) {
    // 어디서부터 페이지를 넘길건지 확인
    let fromStart = n-p > p-1 ? true : false; 
    // 페이지를 몇 번 넘기는 지만 확인하면 되므로 같은 페이지 숫자 중 큰 수인 홀수로 맞춤.
    n = n%2 === 0 ? n+1 : n;
    p = p%2 === 0 ? p+1 : p;
    return fromStart ? (p-1)/2 : (n-p)/2
}
```

discussions탭에서 나온 다른 답,

```
function pageCount(n, p) {
    /*
      n: the number of pages in the book
      p: the page number to turn to
    */

    const pageTurns = Math.floor(p / 2);
    const totalTurns = Math.floor(n / 2);

    /* Returns the total number of page turns it takes to get
    to a page or how many it requires if starting from the back */

    return Math.min(pageTurns, totalTurns - pageTurns);
}
```
