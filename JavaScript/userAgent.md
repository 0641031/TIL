## User agent를 이용한 브라우저 감지

* 브라우저 속도 개선을 위해서 index에 나오는 이미지를 webp로 변경. 
* html에서는 webp를 지원하지 않을 경우 아래와 같이 picture태그 안에 있는 img를 불러온다.
  ```html
  <picture>
  <source srcset="img/awesomeWebPImage.webp" type="image/webp">
  <source srcset="img/creakyOldJPEG.jpg" type="image/jpeg"> 
  <img src="img/creakyOldJPEG.jpg" alt="Alt Text!">
  ```
* 슬라이드 이미지의 경우 스크립트안에서 webp를 지원하는 브라우저인지 확인을 해야함.

---

HTTP 헤더에서 브라우저 정보를 확인 할 수 있다.

```
var userAgent = window.navigator.userAgent;
console.log(userAgent );

//firefox
Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:66.0) Gecko/20100101 Firefox/66.0

//chrome
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 
Chrome/73.0.3683.103 Safari/537.36

//edge
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) 
Chrome/64.0.3282.140 Safari/537.36 Edge/17.17134

//IE
Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; .NET4.0C; .NET4.0E; 
.NET CLR 2.0.50727; .NET CLR 3.0.30729; .NET CLR 3.5.30729; rv:11.0) like Gecko 
```  


IE10까지는 msie로 판별 가능하나, IE11에서는 Trident로 해야한다. ( IE7 이하에서 Trident는 나오지 않음)  


> ※ 참고 : 트라이던트(Trident)는 MS의 IE에서 사용하고 있는 레이아웃 엔진의 이름이며, MSHTML이라고도 합니다. 
> 그리고 이 엔진은 IE가 4.0 버전일 때부터 도입되어 현재까지 사용되고 있습니다. 그러므로 IE 브라우저를 구분해낼 수 있는 유일한 값이기도 합니다. 
> (다른 브라우저에서는 트라이던트 엔진을 사용하지 않으니까요)
>
> 출처: https://ooz.co.kr/67 [이러쿵저러쿵]  



edge에 chrome, safari가 포함되어 있고 chrome에 safari가 포함되어 있기 때문에 if문으로 조건을 줄 때 순서를 
[IE - Edge - 크롬 - 사파리 - 파이어폭스 - 오페라]로 해야함.  


```javascript
var userAgent = window.navigator.userAgent.toLowerCase();

if(userAgent.indexOf('msie') != -1 ||
        userAgent.indexOf('trident') != -1 ||) {
    console.log('Internet Explorer');
} else if(userAgent.indexOf('edge') != -1) {
    console.log('Edge');
} else if(userAgent.indexOf('chrome') != -1) {
    console.log('Google Chrome');
} else if(userAgent.indexOf('safari') != -1) {
    console.log('Safari');
} else if(userAgent.indexOf('firefox') != -1) {
    console.log('FireFox');
} else if(userAgent.indexOf('opera') != -1) {
    console.log('Opera');
} 
```  


indexOf() 메서드는 호출한 String 객체에서 주어진 값과 일치하는 첫 번째 인덱스를 반환하고, 일치하는 값이 없으면 -1을 반환.  



###### reference
* [https://qiita.com/sakuraya/items/33f93e19438d0694a91d](https://qiita.com/sakuraya/items/33f93e19438d0694a91d)
* [https://programmingsummaries.tistory.com/388](https://programmingsummaries.tistory.com/388)
* [https://ooz.co.kr/67](https://ooz.co.kr/67)
* [https://css-tricks.com/using-webp-images/](https://css-tricks.com/using-webp-images/)
