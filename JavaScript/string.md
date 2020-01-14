##  String

1. String.prototype.repeat()

	> str.repeat(count)

	문자열을 주어진 횟수만큼 반복해 붙인 새로운 문자열을 반환

	* count : 0과 양의 무한대 사이의 정수.

	```javascript
	'a'.repeat(5)
	// 'aaa'
	'a'.repeat(-1)
	// Uncaught RangeError: Invalid count value
	```

	IE, Android Webview 지원안함.

1. String.prototype.substring()

	> str.substring(indexStart[, indexEnd])

	시작 인덱스로부터 종료 인덱스전까지 문자열의 부분 문자열을 반환

	* indexStart : 반환 할 문자열의 시작 인덱스
	* indexEnd : 반환 할 문자열의 마지막 인덱스(해당 인덱스의 문자열은 포함하지 않음) optional이고 생략하면 문자열 끝까지 반환. 

	```javascript
	const str = "abcde"
	str.substring(1)
	// 'bcde'
	str.substring(1, 4)
	// 'bcd'
	```

	* indexStart가 indexEnd보다 클 경우, 두개의 인자를 바꾼 것 처럼 동작함. 

	```javascript
	str.substring(4, 1)
	// 'bcd'
	```
	
	* 뒤에서부터 시작하여 문자열을 자르고 싶을 때,

	```javascript
	str.substring(str.length-3)
	// 'cde'
	```


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

