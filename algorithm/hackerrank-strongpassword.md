### [hackerrank - Strong Password](https://www.hackerrank.com/challenges/strong-password/problem)

Louise joined a social networking site to stay in touch with her friends. The signup page required her to input a name and a password. However, the password must be strong. The website considers a password to be strong if it satisfies the following criteria:

* Its length is at least __6__.
* It contains at least one digit.
* It contains at least one lowercase English character.
* It contains at least one uppercase English character.
* It contains at least one special character. The special characters are: !@#$%^&\*()-+

She typed a random string of length __n__ in the password field but wasn't sure if it was strong. Given the string she typed, can you find the minimum number of characters she must add to make her password strong?

Note: Here's the set of types of characters in a form you can paste in your solution:

```
numbers = "0123456789"
lower_case = "abcdefghijklmnopqrstuvwxyz"
upper_case = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
special_characters = "!@#$%^&*()-+"
```


**Input Format**

The first line contains an integer __n__ denoting the length of the string.

The second line contains a string consisting of __n__ characters, the password typed by Louise. Each character is either a lowercase/uppercase English alphabet, a digit, or a special character.

**Output Format**

Print a single line containing a single integer denoting the answer to the problem.


Example: 
```
Input: 
3
Ab1

Output: 
3
```

Explanation

She can make the password strong by adding __3__ characters, for example, $hk, turning the password into Ab1$hk which is strong.

__2__ characters aren't enough since the length must be at least __6__.

---

Answer:
```
function minimumNumber(n, password) {
    let numbers = /[0-9]/;
    let lower_case = /[a-z]/;
    let upper_case = /[A-Z]/;
    let special_characters = /[!@#$%^&*\(\)\-+]/;
    let count = 0;
    if(password.match(numbers)){
        count += 1;
    }
    if(password.match(lower_case)){
        count += 1;
    }
    if(password.match(upper_case)){
        count += 1;
    }
    if(password.match(special_characters)){
        count += 1;
    }
    return Math.max(6-n, 4-count)

}
```

###### reference
* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#Using_special_characters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#Using_special_characters)