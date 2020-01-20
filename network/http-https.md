### HTTP & HTTPS


#### HTTP (HyperText Transfer Protocol)

* www상에서 정보를 주고받을 수 있는 통신규약. 
* 주로 HTML문서를 주고받는데 쓰인다.
* 웹 상에서 클라이언트와 서버간에 요청/응답(request/response)으로 정보를 주고받음.
* http를 통해 전달되는 자료는 http:로 시작하는 url로 조회할 수 있다.
* TCP와 UDT를 사용하며, 80번 포트를 사용한다.
* 왜 80번 포트? 98년에 설립된 기구(ICANN : The Internet Corporation for Assigned Names and Numbers)에 속해있는 IANA(The Internet Assigned Numbers Authority)가 90년에 알려져있던 모든 포트번호를 기술한 문서를 만들었는데, 그 문서에 80번이 없었음. 91년에 팀 버너스리가 HTTP 0.9 문서에서 첫번째 http버전을 발표할 때, port의 기본값을 80으로 기술함.
* Connectionless : 요청을 보내고 서버가 응답하면 바로 연결이 끊긴다. (cookie, session으로 이를 보완)
* Stateless : 연결을 끊는 순간, 클라이언트와 서버의 통신은 끝나며 상태 정보를 유지하지 않는다. 
* 응답코드 : 클라이언트가 서버에 한 요청에 대한 응답

	| :computer: | :speech_balloon: | :page_facing_up:  |
	|---|---|---|
	|2XX |success | 200 : OK, 201 : Created - 요청의 결과로 새로운 리소스가 생성.|
	|3XX |redirection - 요청을 완료하기 위해 redirect가 필요함 | |
	|4XX |client error - 잘못된 요청 |400 : Bad Request - 잘못된 요청으로 서버가 요청을 이해할 수 없음. 404 : Not Found - 요청받은 리소스를 찾을 수 없음. |
	|5XX |server error - 올바른 요청이지만 서버가 응답할 수 없음 | 500 : Internal Server Error - 서버가 처리방법을 모름. |
* 약점 : 평문이기 때문에 도청가능, 통신 상대를 확인하지 않기 때문에 위장 가능, 완전성을 증명할 수 없기 때문에 변조 가능.


#### HTTPS (HyperText Transfer Protocol over Secure Socket Layer)

* HTTP의 보안이 강화된 버전의 통신규약. 통신의 인증과 암호화를 위해 넷스케이프가 개발.
* 기본포트는 443.
* https: 로 시작하는 url 사용.
* 소켓통신에서 일반텍스트를 이용하는 대신, 웹 상에서 정보를 암호화하는 SSL(Secure Socket Layer)이나 TLS(Transfer Layer Security) 프로토콜을 통해 세션데이터를 암호화. (SSL과 TLS 주요목적은 기밀성, 데이터 무결성, ID 및 디지털인증서를 사용한  인증제공)
* 원리 : 공개키 알고리즘 방식.
	client 공개키로 암호화 - server 개인키로 복호화하여 요청처리
* 장점 : 네트워크 상에서 열람, 수정이 불가능하므로 안전.
* 단점 : 암호화 과정이 서버에 부담. 설치 및 인증서에 추가비용 발생. 소켓(데이터를 주고받는 경로) 자체에서 인증하기 때문에 연결이 끊기면 소켓도 끊어져서 재인증에 시간이 소요된다.


###### reference
* [https://github.com/WeareSoft/tech-interview/blob/master/contents/network.md#http와-https](https://github.com/WeareSoft/tech-interview/blob/master/contents/network.md#http와-https)
* [https://creativeworks.tistory.com/entry/HTTP80-HTTPS443-%EC%99%9C-80-443%EB%B2%88%EC%9D%BC%EA%B9%8C-%EC%9D%B4%EC%9C%A0%EB%8A%94](https://creativeworks.tistory.com/entry/HTTP80-HTTPS443-%EC%99%9C-80-443%EB%B2%88%EC%9D%BC%EA%B9%8C-%EC%9D%B4%EC%9C%A0%EB%8A%94)
* [https://ko.wikipedia.org/wiki/HTTP](https://ko.wikipedia.org/wiki/HTTP)
* 우에노 센, 「그림으로 배우는 HTTP & Network Basic」, 이병억 옮김, 영진닷컴(2015)

