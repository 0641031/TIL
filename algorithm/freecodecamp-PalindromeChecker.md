### [JavaScript Algorithms and Data Structures Projects: Palindrome Checker](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/javascript-algorithms-and-data-structures-projects/palindrome-checker/)

* Palindrome (회문, 앞뒤가 똑같은)
> A palindrome is a word, number, phrase, or other sequence of characters which reads the same backward as forward, such as madam or racecar or the number 10801. 
> Sentence-length palindromes may be written when allowances are made for adjustments to capital letters, punctuation, 
> and word dividers, such as "A man, a plan, a canal, Panama!", "Was it a car or a cat I saw?" or "No 'x' in Nixon". 

##### Note
* You'll need to remove all non-alphanumeric characters (punctuation, spaces and symbols) and turn everything into the same case (lower or upper case) in order to check for palindromes.
* We'll pass strings with varying formats, such as "racecar", "RaceCar", and "race CAR" among others.
* We'll also pass strings with special symbols, such as "2A3*3a2", "2A3 3a2", and "2_A3*3#A2".


```
function palindrome(str) {
  var arr = str.replace(/[^A-Za-z0-9]/g,"").toLowerCase().split("");
  for(var i=0;i<arr.length/2;i++ ){
      if(arr[i]!=arr[arr.length-1-i]){
        return false;
     }
  }
  return true;
}
```

1. 처음에 공백을 없애기 위해서, trim()을 사용해보려고 했는데 이건 문자열 앞뒤에 있는 공백에만 해당하기 때문에 여기서는 사용할 수 없음.
2. /[^A-Za-z0-9]/g <- g는 해당하는 모든 문자를 뜻함.
3. 배열의 인덱스가 0부터 시작하는거랑 배열의 길이를 연결해서 생각하지 않아서 arr[arr.length-1-i] 이 부분에서 헤맴. 
4. 배열의 길이만큼 다 해보지 않아도 되기 때문에 i<arr.length/2.
5. 해답에 있던 Basic Code Solution

```
function palindrome(str) {
      return str.replace(/[\W_]/g, '').toLowerCase() ===
             str.replace(/[\W_]/g, '').toLowerCase().split('').reverse().join('');
    }
```
