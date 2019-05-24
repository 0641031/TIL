##  Date

* 일정날짜 이후에 다른 페이지로 리다이렉트하기
* javascript로 현재날짜 가져와서 비교이후에 location.href하면 되지 않을까…?

---

Date객체를 생성하고 console.log로 확인을 해보면
```
Fri May 24 2019 16:14:28 GMT+0900 (Japan Standard Time)
```
이렇게 나온다.

내가 필요한 건, 특정 날짜이후에  페이지를 리다이렉트 하는 것이기 때문에 

```javascript
let now = new Date();
let date = now.getFullYear() + ‘-’ + (now.getMonth()+1) +’-’+ now.getDate();
//result : “2019-5-24”
```

특정 날짜에만 적용을 하는거라면 `date==”기준날짜”`를 조건으로 해도 되겠지만, 타입이 string이기 때문에 이후를 기준으로 하려면 date객체를 그대로 사용해야 한다.

> 만일 아무런 전달값도 없다면, 생성자는 Date 객체가 로컬 시간에 따른 현재 날짜와 시간값을 가지도록 합니다. 
> 만약 전달값 중 일부만 있다면, 나머지 빠진 전달값들은 모두 0이 됩니다. 모든 전달값을 제공하려면 최소한 연도, 월, 일은 포함해야 하며, 
> 시, 분, 초 그리고 밀리초는 생략할 수 있습니다.

`let target = new Date(‘2019-5-24’)` 라고 기준일을 전달하여 객체를 만들어서 확인해보면,
```
Fri May 24 2019 00:00:00 GMT+0900 (Japan Standard Time)
```
위와 같이 확인 가능.

그리고 Date객체로 비교가 가능하기 때문에 부등호로 target 이후인지 아닌지 조건을 걸고 redirect해주면 된다. 
```
console.log(now == target);
// false 시,분,초 단위까지 일치하지 않기 때문에 
console.log(now>= target);
// true target보다 현재가 이후이기 때문에
```

~~페이지가 다 로드되고 스크립트가 실행되기 때문에 결국은 컨트롤러에서 해결함~~ 


###### reference
* [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date)

