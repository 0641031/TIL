### async, await

<sub>차트를 그리는 메소드에 async를 붙이고 차트에 필요한 데이터 변수를 할당할 때, 프로미스 객체를 반환하는 함수에 await를 붙여서 사용하고 있다. 
</sub>

좀 더 간단하게 비동기처리를 할 수 있도록 ES8에서 도입됨.

```javascript
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  var result = await resolveAfter2Seconds();
  console.log(result);
  // expected output: 'resolved'
}
```

await를 붙인 비동기처리 메소드는 반드시 **프로미스 객체를 반환**해야 한다. promise를 여러개 사용하는 코드를 처리할 때보다 코드의 가독성이 좋아진다. 


* 예외처리

```
async function asyncCall() {
  console.log('calling');
  try{
   var result = await resolveAfter2Seconds();
    console.log(result);
    // expected output: 'resolved'

  }catch(error){
    console.log(error
  }
 }

```

###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/async_function)
* [https://joshua1988.github.io/web-development/javascript/js-async-await/](https://joshua1988.github.io/web-development/javascript/js-async-await/)

