### [Leetcode - Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.


Example 1: 
```
Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
```

Example 2: 
```
Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
```

먼저 linked list의 길이를 구하고 중간값을 찾았음.

Answer:
```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var middleNode = function(head) {
    let list = head;
    let len = 0;
    while(list !== null){
        list = list.next
        len += 1
    }
    list = head;
    len = Math.floor(len/2)
    for(let i=0; i<len; i++){
        list = list.next
    }
    return list
};
```

두개의 포인트를 이용하는 방법이 있었다! :eyes: 

next를 가르키는 slow, next.next를 가르키는 fast 두가지를 사용하면 fast가 끝날 때, slow가 중간값을 가르키게 된다.

```
var middleNode = function(head) {
    let slow = fast = head;
    while(fast !== null && fast.next !== null){
        fast = fast.next.next;
        slow = slow.next;
    }
    return slow
};
```

###### reference
* [https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3290/discuss/426521/Javascript-two-pointers-(fast-and-slow)](https://leetcode.com/explore/challenge/card/30-day-leetcoding-challenge/529/week-2/3290/discuss/426521/Javascript-two-pointers-(fast-and-slow))
