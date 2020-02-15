##  String

1. String.prototype.padStart()

	> str.padStart(targetLength [, padString])

	현재 문자열의 시작을 다른 문자열로 채워, 주어진 길이를 만족하는 새로운 문자열을 반환. 문자의 왼쪽부터 채워짐.

	* targetLength : 반환 될 문자열의 길이. 현재 문자열길이보다 작은 숫자를 입력하면 현재 문자열 그대로 반환됨.
	* padString : 현재 문자열에 채워넣을 다른 문자열.

	```javascript
	'abc'.padStart(5,'*')
	// '**aaa'
	'abc'.padStart(2,'*')
	// 'aaa'
	```

	IE 지원안함.

	String.prototype.padEnd()는 문자의 오른쪽부터 문자열을 채운다는 것만 빼고 padStart()와 동일하게 동작함.

	

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)

