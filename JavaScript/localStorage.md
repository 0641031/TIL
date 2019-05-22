## Window​.local​Storage


* [https://qiita.com/moonglows76/items/358ef3cd1566c38ece3a](https://qiita.com/moonglows76/items/358ef3cd1566c38ece3a)

Vue로 todolist를 만들어보려고 구글링하다가 그나마 간단해 보이는, 코드가 대부분 이해가 되는 걸 찾아서 혼자 하다가 막히면 참고하면서 만들었다. 그런데 내가 만들던 건 새로고침을 하면 데이터가 없어지는데 참고하던 건 새로고침을 해도 데이터가 저장이 되길래 따라하다가 알게 되었다.

---

* [https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage
)

> localStorage는 sessionStorage와 비슷합니다. 유일한 차이점은 localStorage에 저장된 데이터는 만료 기간이 없지만,
> sessionStorage에 저장된 데이터는 세션이 끝나면(브라우저가 종료되면) 지워진다는 것입니다.

localStorage메소드로 로컬의 storage객체에 접근이 가능하다.


* [Storage](https://developer.mozilla.org/ko/docs/Web/API/Storage)

> Web Storage API의 Storage인터페이스는 특정 도메인의 세션 혹은 로컬 스토리지에 접근할 수 있게 한다.



```javascript
//Storage객체에 데이터를 저장할 때
localStorage.setItem('myCat', 'Tom');

//Storage객체에서 데이터를 가져올 때
var cat = localStorage.getItem('myCat');

//특정 데이터를 지울 때
localStorage.removeItem('myCat');

//전체 데이터를 지울 때
localStorage.clear();
```  

key와 value값은 항상 string이어야 한다. 그렇기 때문에 객체를 저장하기 위해서는 JSON.stringify를 사용해야 하고, 받을 때는 JSON.parse를 사용한다.

\
![localStorage](https://i.imgur.com/uL1W6Bz.png)

저장된 데이터는 크롬을 기준으로 developer tools - application - local storage에서 확인 가능하다.

(MDN문서를 한글로 볼 때는 번역이 되다 만 것도 있으므로 원본을 꼭 확인하는 편이 좋음.)



###### reference
* [https://www.zerocho.com/category/HTML&DOM/post/5918515b1ed39f00182d3048](https://www.zerocho.com/category/HTML&DOM/post/5918515b1ed39f00182d3048
)
* [https://developer.mozilla.org/ko/docs/Web/API/Storage](https://developer.mozilla.org/ko/docs/Web/API/Storage)
* [https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
