### CORS (Cross Origin Resource Sharing)


* HTTP요청은 기본적으로 Cross-site HTTP요청이 가능한데(img태그에서 다른 도메인의 이미지호출, link태그로 다른 도메인의 css 호출, CDN사용 등), `<script>`태그로 둘러싸여 있는 스크립트에서 생성된 request는same-origin-policy를 적용받기 때문에 불가능하다.
	
	same-origin-policy : 보안이슈로 프로토콜, 호스트명, 포트가 같아야만 요청 가능.
* AJAX(Asynchronous JavaScript and XML)가 널리사용되면서, `<script>`태그내의 XMLHttpRequest에 대한 요구가 많아짐.
* 웹브라우저에서 외부 도메인 서버와 통신하기위한 방식을 표준화 함 => CORS 헤더의 규칙으로 결정

#### 요청의 종류

1. simple request
	* GET, HEAD, POST 중에 한 방식.
	* POST일 때, Content-Type이 application/x-www-form-urlencoded, multipart/form-data, text/plain 중에 하나여야 함.
	* 커스텀 헤더 전송이 불가능.
	* 서버에 1번 요청하고 서버도 1번 응답함.

2. Preflight Request
	* 위의 simple request가 아닌 경우. (GET, HEAD, POST가 아니고, POST일 때, Content-Type이 위 세가지가 아니고…)
	* 예비요청 / 본요청 나뉘어서 전송.
	* 예비요청을 보내고 서버가 응답이 가능한지 확인한 후, 본요청을 보냄.

3. Credential 
	* HTTP Cookie와 HTTP Authentication 정보를 인식하게 해주는 요청.
	* `.withCredentials = true`로 지정.
	* 서버는 응답헤더에 `Access-Control-Allow-Credential: true`를 포함해야 하고, `Access-Control-Allow-Origin`헤더값에는 \*가 오면 안되고, 특정도메인이 와야한다.

4. Non-Credential
	* `.withCredentials = false`인 경우. 기본값이 false임.


#### CORS관련 Headers

Access-Control...로 시작하는 헤더는 CORS에 관한 것임.

1. Request Headers
	* Origin : cross-site 요청을 날리는 도메인 URI.
	* Access-Control-Request-Method : 예비요청에 포함. 본요청에 어떤 메소드를 사용할 지 서버에 알려줌.
	* Access-Control-Request-Headers : 예비요청에 포함. 본요청에서 어떤 HTTP Header를 사용할 지 서버에 알려줌. 

2. Response Headers
	* Access-Control-Allow-Origin : 지정된 도메인으로부터의 요청만 서버의 리소스에 접근 가능. (\*경우는 전부 접근 가능)
	* Access-Control-Max-Age : 예비요청의 결과가 캐쉬에 얼마나 오랫동안 남아있는지 설정.
	* Access-Control-Allow-Credential : `.withCredentials = true` 인데, 이 항목이 명시되지 않았다면, 브라우저가 응답을 무시한다.



###### reference
* [https://medium.com/@buddhiv/what-is-cors-or-cross-origin-resource-sharing-eccbfacaaa30
](https://medium.com/@buddhiv/what-is-cors-or-cross-origin-resource-sharing-eccbfacaaa30
)
* [https://zamezzz.tistory.com/137](https://zamezzz.tistory.com/137)
* [https://brownbears.tistory.com/336](https://brownbears.tistory.com/336)
