### [JavaScript Algorithms and Data Structures Projects: Caesars Cipher](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/javascript-algorithms-and-data-structures-projects/caesars-cipher)

* Caesars Cipher
> 암호학에서, 가장 간단하고 널리 알려진 치환 암호화 기술 중 하나.
> 암호화하고자 하는 내용을 알파벳별로 일정한 거리만큼 밀어서 다른 알파벳으로 치환하는 방식. 
> Julius Caesar의 이름을 따서 만들어 졌다.

##### Note
* A common modern use is the [ROT13](https://en.wikipedia.org/wiki/ROT13) cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.
* All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.


```
function rot13(str) { 
  var arr = str.split("");  
  var answer='';
  for(var i= 0; i<arr.length;i++){
    if(arr[i].match(/[A-Z]/)){
      if(arr[i].charCodeAt()<'N'.charCodeAt()){      
       answer+=String.fromCharCode(arr[i].charCodeAt()+13);
      }else{
        answer+=String.fromCharCode(arr[i].charCodeAt()-13);
      }
    }else{
      answer+=arr[i];
    }
  }
  return answer;
}
```

1. 13을 밀거나 당기면 되니까 아스키코드를 생각 함.
2. 정규표현식을 바로 전 문제에서 공부했기 때문에 수월하게 사용할 수 있었다.
3. 아스키코드로 변경했을 때의 숫자를 모르기 때문에 연결된 ROT13 링크에서 접한 정보로 해결하려고 함.
4. [String.charcodeAt()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt) : charCodeAt() 메서드는 주어진 인덱스에 대한 UTF-16 코드를 나타내는 0부터 65535 사이의 정수를 반환합니다.
5. [String.fromCharCode()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode) : fromCharCode() 메서드는 UTF-16 코드 유닛의 시퀀스로부터 문자열을 생성해 반환합니다.

~~더 효율적인 방법이 있을 것 같다...~~
