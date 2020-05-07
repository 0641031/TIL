### [hackerrank - Making Anagrams](https://www.hackerrank.com/challenges/making-anagrams/problem)

We consider two strings to be anagrams of each other if the first string's letters can be rearranged to form the second string. In other words, both strings must contain the same exact letters in the same exact frequency. For example, bacdc and dcbac are anagrams, but bacdc and dcbad are not.

Alice is taking a cryptography class and finding anagrams to be very useful. She decides on an encryption scheme involving two large strings where encryption is dependent on the minimum number of character deletions required to make the two strings anagrams. Can you help her find this number?

Given two strings, __s1__ and __s2__, that may not be of the same length, determine the minimum number of character deletions required to make  and  anagrams. Any characters can be deleted from either of the strings.

For example, __s1 = abc__ and __s2 = amnop__. The only characters that match are the __a__'s so we have to remove __bc__ from __s1__ and __mnop__ from __s2__ for a total of __6__ deletions.


**Function Description**

Complete the makingAnagrams function in the editor below. It should return an integer representing the minimum number of deletions needed to make the strings anagrams.

makingAnagrams has the following parameter(s):

* s1: a string
* s2: a string

**Input Format**

The first line contains a single string, __s1__.
The second line contains a single string, __s2__.

**Output Format**

Print a single integer denoting the minimum number of characters which must be deleted to make the two strings anagrams of each other.


Example: 
```
Input: 
cde
abc

Output: 
4
```

Explanation

We delete the following characters from our two strings to turn them into anagrams of each other:

1. Remove d and e from cde to get c.
2. Remove a and b from abc to get c.

We had to delete __4__ characters to make both strings anagrams.

---

Answer:
```
function makingAnagrams(s1, s2) {
    let arr1 = s1.split('');
    let arr2 = s2.split('');
    for(let i=0; i<arr1.length; i++){
    	// s1의 요소가 s2에 있을 경우, 삭제
        if(arr2.indexOf(arr1[i]) > -1 ){
            arr2.splice(arr2.indexOf(arr1[i]),1)
            arr1.splice(i,1)
            i -= 1;
        }
    }
    // 아나그램을 삭제한 나머지 요소들의 합을 반환
    return arr1.length + arr2.length;
}
```
