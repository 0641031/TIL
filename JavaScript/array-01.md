##  Array

javascript 알고리즘을 공부하다보면 array를 자주 사용하게 되는데, map이랑 filter랑 헷갈린다. 정리를 하자.

---

아래 정리할 모든 내장객체의 매개변수는 동일하다.

> arr.map(callback(currentValue[, index[, array]])[, thisArg])

index, array(호출한 배열), thisArg는 optional


1. Array.map()
map() 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 **새로운 배열을 반환**.

```javascript
const arr = [1,2,3,4,5];
arr.map(i=>i*2);
// Array(5) [ 2, 4, 6, 8, 10 ]
```


2. Array.forEach()

forEach() 메서드는 주어진 함수를 배열 요소 각각에 대해 실행. **반환값이 undefined**.

```javascript
const arr = [1,2,3,4,5];
const answer = [];
arr.forEach(i=>answer.push(i*2));
console.log(answer);
// Array(5) [ 2, 4, 6, 8, 10 ]
```


3. Array.filter()

filter() 메서드는 주어진 함수의 테스트를 통과하는 모든 요소를 모아 **새로운 배열로 반환**.

```javascript
arr.filter(i=>i>2);
// Array(3) [ 3, 4, 5 ]
```

map이랑 헷갈려서 사용하면…

```javascript
arr.map(i=>i>2)
// Array(5) [ false, false, true, true, true ]
```
이런 결과가 나온다...:neutral_face:


4. Array.every()

every() 메서드는 배열 안의 **모든 요소**가 주어진 판별 함수를 통과하는지 테스트.
callback이 모든 배열 요소에 대해 참인 값을 반환하는 경우 true, 그 외엔 false.

```javascript
arr.every(i=>i<5)
// false
```


5. Array.some()

some() 메서드는 배열 안의 **어떤 요소**라도 주어진 판별 함수를 통과하는지 테스트. 빈 배열에서 호출하면 무조건 false를 반환. 
callback이 어떤 배열 요소라도 대해 참인 값을 반환하는 경우 true, 그 외엔 false.

```javascript
arr.some(i=>i<5);
// true
```


반환값을 숙지하고 있는게 중요한 것 같다. 그게 제일 헷갈리는 듯.

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date)

