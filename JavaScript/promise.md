### Promise

<sub>현재 하고 있는 프로젝트는 데이터를 차트로 보여주는 페이지가 많아 Promise가 많이 쓰인다. 대충 감으로만 알고 있다가 개념을 확실히 하기 위해 정리함.</sub>


* ES6에서 비동기 처리를 위해 도입한 표준내장객체. (비동기 처리 : 특정 코드의 실행이 완료될 때까지 기다리지 않은 다음 코드를 실행하는 자바스크립트의 특성. [참고](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/))

1. Promise 생성자 함수를 통해 객체를 만들어 사용한다. 생성자 함수는 비동기 작업을 수행할 함수를 인자로 받고 이 함수는 resolve, reject 함수를 인자로 전달받는다.

	```javascript
	const myFirstPromise = new Promise((resolve, reject) => {
	  if (/* 성공 */) {
	    resolve('result'); //비동기 처리의 결과를 인자로 전달
	  }
	  else { /* 실패 */
	    reject('failure reason'); //비동기 처리의 에러메시지를 인자로 전달.
	  }
	});
	```

2. Promise는 비동기 처리의 상태정보를 갖는다.
	* pending : 비동기 처리가 수행되지 않은 상태. (resolve, reject가 호출되지 않음)
	* fulfulled : 비동기 처리가 수행되어 성공한 상태 .(resolve가 호출됨)
	* rejected : 비동기 처리가 수행되어 실패한 상태. (reject가 호출됨)
	* settled : 비동기 처리가 수행되어 성공 또는 실패한 상태. (resolve 또는 reject가 호출됨)

3. resolve가 호출되면 비동기 처리의 결과를 인자로 전달하고, reject가 호출되면 에러메시지를 인자로 전달한다.

4. 비동기 처리가 수행되면 후속처리 메소드를 통해 결과를 처리함.
	* then메소드는 두개의 콜백함수를 인자로 전달 받음. 첫번째 콜백함수는 resolve가 호출된 상태(성공시)에서 호출되고 두분째 콜백함수는 reject함수가 호출된 상태(실패시)에서 호출된다. 
	* catch는 비동기처리나 then 메소드에 에러가 발생하면 호출됨.

	```javascript
	let myFirstPromise = new Promise((resolve, reject) => {  
	   setTimeout(function(){
	    resolve("Success!"); // Yay! Everything went well!
	  }, 1000);
	});
	myFirstPromise.then((successMessage) => {
	  console.log("Yay! " + successMessage);
	});
	// 1초 후, Yay! Success! 가 출력됨.
	```

5. 비동기처리의 에러는 then의 두번째 인자, catch메소드 양쪽에서 다 캐치할 수 있다. 그러나 then 메소드 안에서도 에러가 발생할 수 있기 때문에 에러처리는 catch에서 하는게 효율적이다. 

6. 프로미스 체이닝 : then 메소드가 promise 객체를 반환하도록 하여 여러개의 프로미스를 연결하여 사용 가능. 

7. Promise.all : 프로미스가 담겨있는 인자를 배열 등의 이터러블 형태로 전달 받고 수행 결과도 배열로 받는다. 인자로 전달할 때의 순서가 보장됨! 첫번째로 전달한 인자의 처리속도가 느려도 첫번째 인자로 반환됨. 프로미스 처리가 하나라도 실패하면 reject가 실행됨.
	```javascript
	Promise.all([
	  new Promise(resolve => setTimeout(() => resolve(1), 3000)), // 1
	  new Promise(resolve => setTimeout(() => resolve(2), 2000)), // 2
	  new Promise(resolve => setTimeout(() => resolve(3), 1000))  // 3
	]).then(console.log) 
	  .catch(console.log);
	  // 3초 후, [1, 2, 3]이 출력됨.
	```


Promise.all은 지금 하는 프로젝트에서 하나의 컴포넌트에서 여러개의 데이터가 필요할 때 사용하고 있고, 체이닝은 vue-devmeetup할 때, firebase를 사용하면서 써본 적이 있음. (~~그때는 몰랐지만~~) 

firebase에서 사용하는 [동기, 비동기, 프라미스](https://firebase.google.com/docs/functions/terminate-functions?hl=ko) 



###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
* [https://poiemaweb.com/es6-promise](https://poiemaweb.com/es6-promise)
* [https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)
