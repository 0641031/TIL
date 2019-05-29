## $(function(){ 그리고 $(window).on(‘load’,function(){ 뭐가 먼저 실행될까.

* 스크립트 실행순서의 영향으로 `Uncaught TypeError`에러 출력 후,`$(function(){`를 `$(window).on(‘load’,function(){`로 변경 후 문제가 해결 되었다.
* 테스트 해볼까.

---

* $(function(){} : DOM트리의 구축이 완료되면 실행.
* $(window).on(‘load’,function(){} : 이미지 영상 등 관련데이터를 모두 읽은 다음에 실행.

무조건 ready가 먼저 실행될 줄 알았다. jQuery는 최신버전(3.4.1)으로 함. 

```javascript
$(function(){
    console.log("$(document).ready(){ 1")
})

$(function(){
    console.log("$(document).ready(){ 2")
})

$(window).on('load',function(){
    console.log("$(window).on('load',function(){ 1")
})

$(window).on('load',function(){
    console.log("$(window).on('load',function(){ 2")
})
```

실행결과가

![ready and load _ test 1](https://i.imgur.com/PpU88QP.png)

응…?
HTML코드 안에는 아무것도 입력하지 않았다. 

> window 객체는 DOM 문서를 포함한 브라우처의 창을 나타냅니다. document 속성은 브라우저 창에 로드된 DOM 문서를 가리킵니다. 
> 주어진 문서에 대한 window는 document.defaultView 속성을 사용하여 얻을 수 있습니다.
>
> [https://developer.mozilla.org/ko/docs/Web/API/Window](https://developer.mozilla.org/ko/docs/Web/API/Window)

window객체가 DOM문서를 포함하고 있는데 window.load가 먼저 실행이 될 수도 있다니. 이해가 안되는데..? 
구글링을 해보면 document.ready와 window.load에 대한 차이점에 대한 글이 엄청 많은데 7,8년 전 글이 많다. 
혹시나 해서 위의 코드 그대로 jQuery의 버전만 2.x snippet 혹은 1.x.snippet으로 실행하면 
예상했던대로 document.ready가 먼저 출력이 됐다. 업데이트에 뭐가 있는거 같다. 

\
계속 구글링함…

그러다 찾았다.

![github issue](https://i.imgur.com/e1i9eBA.png)

[https://github.com/jquery/jquery/issues/3197](https://github.com/jquery/jquery/issues/3197)

ready가 너무 느리다는 issue. 그런데 이제 ready핸들러는 비동기로 작동한다는 답변이 달렸다. 
2016년 6월에 제이쿼리 3.0을 릴리즈했고 [jQuery Core 3.0 Upgrade Guide](https://jquery.com/upgrade-guide/3.0/#breaking-change-document-ready-handlers-are-now-asynchronous)에 자세하게 나와있다.

> 핸들러는 이제 독립적으로 실행되기 때문에 다른핸들러에 영향을 주지 않는다.

```javascript
$(function(){
    console.log("$(document).ready(){ 1")
})
$(function(){
    test()
})
$(function(){
    console.log("$(document).ready(){ 2")
})
```

test라는 함수를 정의하지 않고 다음과 같은 코드를 실행하면, 3.0이하의 버전에선

![ready and load _ test 2](https://i.imgur.com/Eryr7CI.png)


3.0 이상에서는


![ready and load _ test 3](https://i.imgur.com/aVqK0kU.png)


이런 결과를 확인 할 수 있다. 
3.0 이전에는 정의되지 않은 함수가 호출되었기 때문에 에러난 시점에서 멈추고 그 이하의 코드를 실행하지 않지만 
3.0 이후에는 핸들러가 독립적으로 작동하기 때문에 다른 코드에 영향을 주지 않고 아래의 코드도 실행이 되는 걸 확인할 수 있다.


다시 실행순서로 돌아가서, 예전의 document.ready처럼 DOM트리 구축이 완료된 시점을 활용하고 싶다면
`document.addEventListener("DOMContentLoaded", function(event) {})` 이걸 사용하면 될 것 같다. (단, IE8이하에서는 지원하지 않음)
호출순서는 다음과 같다. 


![ready and load _ test 4](https://i.imgur.com/Ab4LU6n.png)


그런데 HTML에 코드가 없는 경우의 순서가 이렇고, 외부이미지 경로를 포함한 img태그 하나를 넣어서 테스트 해보니 
document.ready가 먼저 호출됐다. 그냥 텍스트만 포함한 코드는 오만줄이 넘어도 window.load가 먼저 실행됨. 


###### reference
* [DOM이란 무엇인가?](https://velog.io/@godori/DOM%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)
* [순수 자바스크립트로 제이쿼리 ready() 대체하기](https://github.com/codepink/codepink.github.com/wiki/%EC%88%9C%EC%88%98-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-%EC%A0%9C%EC%9D%B4%EC%BF%BC%EB%A6%AC-ready()-%EB%8C%80%EC%B2%B4%ED%95%98%EA%B8%B0)
* [문서의 로드시점 - onload, DOMContentLoaded](https://webdir.tistory.com/515)
