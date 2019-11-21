### Javascript의 this


java에서 this는 자기자신을 가리키지만, javascript에서 this는 함수의 호출방식에 따라 this에 바인딩되는 객체가 달라진다.

**함수를 정의할 때 정해지는게 아니고, 호출할 때 정해진다.**

 

1. 기본적으로 함수호출에서 this는 전역객체에 바인딩 된다. (‘use strict’일 때는 undefined) 이는 함수 안에서도 마찬가지. console에서 확인을 해보면 window가 확인됨. (터미널의 경우 global)

2. 함수가 객체의 프로퍼티 값이면 메소드로 호출되는데 이때 this는 메소드를 소유한 객체가 된다. 그러나 메소드 안의 내부함수는 메소드로 호출되는게 아니라 함수호출이기 때문에 this는 window가 됨.

3. new 키워드를 사용하는 경우, 함수 내부의 this는 새로 생성된 객체를 가르킴.
	```
	function Person(name){
		console.log(this)
		this.name = name;
		console.log(this);
	}
	new Person(“billy”);
	//Test {}
	//Test {name: "billy"}
	```
	첫번째 console.log(this)가 빈객체인 이유는 [참조](https://poiemaweb.com/js-this#31-%EC%83%9D%EC%84%B1%EC%9E%90-%ED%95%A8%EC%88%98-%EB%8F%99%EC%9E%91-%EB%B0%A9%EC%8B%9D)

	<sub>자바와 달리 자바스크립트에는 생성자함수의 형식이 정해진 것이 아니라, 함수에 new 를 붙여서 호출하면 생성자 함수로 동작하므로, 첫번째 문자를 대문자로 하여 구별하는게 일반적</sub>

4. ES6의 화살표함수에서는 함수를 포함하는 scope의 this를 계승받는다. (Lexical this) call, bind, apply등으로 컨텍스트를 바꿔도 효과없음.

5. apply, call, bind를 사용할 때, this
	* apply : 함수객체의 메소드로 함수 실행방법 중 하나. 문맥을 수정하기 위해 사용함. 일반함수의 경우 호출할 때 this가 정해지지만 apply를 사용하면 할당하는 첫번째 인자가 this가 된다.
	* call : apply와 비슷하지만 전달받는 매개변수가 다름. apply경우 유사배열객체를 받고 call의 경우 호출되는 함수에 전달 될 매개변수를 하나씩 받음.
	```
	const billy = {
		name : "billy"
	}
	function updateMemberInfo(age, hobby){
		this.age = age;
		this.hobby = hobby;
	}
	updateMemberInfo.call(billy, 65, "reading");
	// apply를 사용하려면 updateMemberInfo.apply(billy, [65, "reading"])
	console.log(billy) 
	// {name: "Billy", age: 65, hobby: "reading"}
	```
	* bind : 새로운 함수를 생성. 첫번째 인자로 바인딩함수가 대상함수의 this에 값을 전달함. 



#### Lexical Scope?

함수를 어디에 선언했는지에 따라 상위 스코프가 결정되는 것을 말함. 함수를 어디서 호출했는지는 스코프결정에 영향이 없음.

```
const name = "billy";
functin setName(){
	const name = "elliot";
	getName();
	
}
function getName(){
	console.log(name)
}
setName();
getName();
// billy
// billy
```

getName() 의 상위스코프가 전역이기 때문에 setName함수 안에서 선언한 name이 아니라 전역에서 선언한 billy가 두 번 출력됨.




###### reference
* [https://poiemaweb.com/js-this](https://poiemaweb.com/js-this)
* [https://github.com/yangshun/front-end-interview-handbook/blob/master/Translations/Korean/questions/javascript-questions.md#this가 JavaScript에서 어떻게 작동하는지 설명하세요.](https://github.com/yangshun/front-end-interview-handbook/blob/master/Translations/Korean/questions/javascript-questions.md#this%EA%B0%80-javascript%EC%97%90%EC%84%9C-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EC%A7%80-%EC%84%A4%EB%AA%85%ED%95%98%EC%84%B8%EC%9A%94
)
* [https://ibrahimovic.tistory.com/29](https://ibrahimovic.tistory.com/29)
