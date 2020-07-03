##  Set


Set은 값 콜렉션으로, 삽입 순서대로 요소를 순회할 수 있고, set 안의 값은 유일함. 


```javascript
const set = new Set();

// 요소 추가
set.add("Harry"); // Set(1) {"Harry"}
set.add(1); // Set(2) {"Harry", 1}
set.add(1); // Set(2) {"Harry", 1}, 동일한 값은 추가되지 않음

// 크기
set.size // 2

// 요소 확인
set.has("Harry"); // true

// 요소 삭제
set.delete(1); // true

// 유일한 값이면 객체도 추가 가능.
set.add({1: "Philosopher's Stone"}); 

// 반복문
set.forEach((value) => {
	console.log(value); 
})
// "Harry"
// {1: "Philosopher's Stone"}

// 가지고 있는 요소의 순서대로 iterator객체를 반환.
set.values(); // SetIterator {"Harry", {1: "Philosopher's Stone"}}
set.keys(); // SetIterator {"Harry", {1: "Philosopher's Stone"}}

// 배열을 set으로 변환하면 중복값이 제거됨
const set2 = new Set([1, 2, 3, 3, 4]); // Set(4) {1, 2, 3, 4}

// set객체를 배열로 변환
Array.from(set2); // [1, 2, 3, 4]
```

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Set](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Set)