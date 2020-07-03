##  Map

1. Map : 키-값 쌍을 저장하고, 각 쌍의 삽입순서도 기억하는 콜렉션. 키, 값에 아무 값이나 올 수 있다.

2. Object와의 차이점

	* Object의 키는 String이나 Symbol이어야 한다. 
	* Map의 정렬되어 삽입순서로 반복문이 진행되지만, Object는 정렬되지 않는다.
	* Map의 항목수는 size로 쉽게 알아낼 수 있지만, Object는 직접 알아내야 한다.
	* Map은 바로 반복문을 사용할 수 있지만, Object의 경우는 배열을 만들어야 반복문을 사용할 수 있다.
	* key - value 추가, 제거에 Map이 성능이 더 좋다.


```javascript
const map = new Map();

// 값 설정
map.set("Harry Potter 1", "Philosopher's Stone");
map.set("Harry Potter 2", "Chamber of Secrets");
map.set("Harry Potter 3", "Prisoner of Azkaban");

// 크기ac
map.size // 3

// 값 확인
map.get("Harry Potter 1");// "Philosopher's Stone"

// 모든 키들을 순서대로 가지고 있는 iterator객체를 반환.
map.keys(); // MapIterator {"Harry Potter 1", "Harry Potter 2", "Harry Potter 3"}

// 반복문
map.forEach((value, key) => {
	console.log(key + " - " + value); 
})
// Harry Potter 1 - Philosopher's Stone
// Harry Potter 2 - Chamber of Secrets
// Harry Potter 3 - Prisoner of Azkaban

// 주어진 키가 있는지 확인
map.has("Harry Potter 1"); // true
map.has("Prisoner of Azkaban"); // false

// 주어진 키와 해당하는 값 삭제
// map.has("Harry Potter 1")의 값을 반환함.
map.delete("Harry Potter 1"); // true
```

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map)

