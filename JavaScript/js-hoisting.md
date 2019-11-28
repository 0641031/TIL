### Javascript의 Hoisting


> 자바스크립트는 ES6의 let, const를 포함하여 모든 선언(var, let, const, function, function, class)을 호이스팅(Hoisting)한다.


* Hoisting이란?

호이스팅이란 모든 **선언문**이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성을 말한다. 즉, 자바스크립트는 모든 선언문(var, let, const, function, function, class)이 선언되기 이전에 참조 가능하다.


```javascript
printName("billy");

function printName(name){
	console.log(name);
}
// billy

printNickname("dancing billy");

var printNickname = function(nickname){
	console.log(nickname);
}
//Uncaught TypeError: printNickname is not a function
```

printName과 같은 함수선언문의 경우 함수 호이스팅의 적용되어 함수선언, 초기화, 할당이 한꺼번에 이루어진다. 그러나 printNickname의 경우 함수 호이스팅이 아닌, 변수 호이스팅이 적용됨. 변수 호이스팅은 선언, 초기화와 할당이 분리되어 진행된다, 


* 선언문만 scope의 선두로 옮겨진다?


```javascript
console.log(name);
//undefined
var name = "billy";

console.log(name);
//billy

console.log(nickname);
Uncaught ReferenceError: nickname is not defined
```

맨 처음 console.log(name)에서 undefined라고 출력이 된다는 건, name이라는 변수선언과 undefined로 초기화까지는 됐다는 것을 의미한다. 선언하지 않은 변수의 경우는 레퍼런스에러가 발생함.


###### reference
* [https://poiemaweb.com/js-function](https://poiemaweb.com/js-function)
* [https://lazymankook.tistory.com/93?category=817664](https://lazymankook.tistory.com/93?category=817664)
