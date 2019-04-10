### [Intermediate Algorithm Scripting: Binary Agents](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/intermediate-algorithm-scripting/binary-agents)

* binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111") should return "Aren't bonfires fun!?"

```
function binaryAgent(str) {
  var arr = str.split(" ");
  var answer ="";
  for(var i=0;i<arr.length;i++){
    answer+=String.fromCharCode(parseInt(arr[i],2)).toString();
  }
  return answer;
}
```

1. [parseInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) 
  > parseInt(string, radix);
  
  parseInt(그저 integer로 형변환하는 건 줄 알았는데...)두번째 매개변수로 기수 설정 가능.

2. [String.fromCharCode()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)
  : UTF-16 코드 유닛의 시퀀스로부터 문자열을 생성해 반환.
  
  2진수의 숫자를 10진수의 숫자로 바꾸고, 아스키코드의 해당 문자로 변환
