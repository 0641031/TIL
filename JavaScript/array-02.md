##  Array

1. Array.prototype.splice()

	> array.splice(start[, deleteCount[, item1[, item2[, ...]]]])

	배열에서 몇 번째 요소를 삭제할 때 주로 사용했기 때문에 보통 매개변수를 두개만 사용하는 경우가 많았다. 

	```javascript
	const arr = [1, 2, 3, 4, 5];
	arr.splice(2, 1); //2번 인덱스(0부터 시작하므로 3을 가르킴)부터 시작해서 1개를 삭제.
	// Array(4) [1, 2, 4, 5]
	```

	세번째 매개변수까지 쓰면 삭제가 아니라 교체가 된다. 
	
	```javascript
	const arr = [1, 2, 3, 4, 5];
	arr.splice(2, 1, 6); //2번 인덱스(0부터 시작하므로 3을 가르킴)부터 시작해서 1개를 삭제하고 6을 추가. 
	// Array(5) [1, 2, 6, 4, 5]
	arr.splice(2, 0, 6);
	// Array(6) [1, 2, 3, 6, 4, 5] // 삭제할 요소의 갯수가 0이므로 추가가 됨.
	```

	제거한 요소를 담은 배열을 반환함.

2. Array.prototype.reduce()

	> arr.reduce(callback[, initialValue])

	* callback : 배열의 각 요소에 실행할 함수. 이 callback함수에서 4가지 인수를 받는다.
		1. accumulator : 콜백의 반환값 누적. 
		2. currentValue : 처리할 현재 요소.
		3. currentIndex : 처리할 현재 요소의 인덱스.
		4. array : reduce를 호출한 배열.
	* initialValue : 맨 처음 콜백함수를 호출할 때 첫번째 인수에게 제공하는 값. 없으면 배열의 첫번째 요소를 사용함.
	
	```javascript
	const arr = [1, 2, 3, 4, 5];
	arr.reduce((a,b) => { return a+b });
	// 15
	```
	가장 흔하게 사용되는 배열의 총합 구하기.

3. Array.prototype.slice()

	> arr.slice([begin[, end]])

	arr의 begin부터 end까지(end는 미포함)의 복사본을 새로운 배열 객체로 반환. 원본 배열은 수정되지 않음.

	```javascript
	const arr = [1, 2, 3, 4, 5];
	arr.slice(1);
	// (4) [2, 3, 4, 5]
	arr.slice(1,3);
	// (2) [2, 3]
	```

	* begin의 기본값은 0. end값만 입력하고 싶을 때는 undefined를 넣으면 기본값이 들어감. 음수를 넣으면 배열의 끝에서부터의 길이를 나타낸다.
	* end의 기본값은 arr.length. 배열의 길이보다 큰 값이 들어가도 배열의 길이가 들어감. 

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference)

