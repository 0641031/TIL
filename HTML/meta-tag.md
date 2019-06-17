## meta tag

크롬 개발자 모드에서 디바이스 변경했는데 반응형으로 안보인다… 원래 있던 코드 수정한다고 css, js 등이 링크되어있던 head를 마구잡이로 삭제하다가… viewport태그를 지운 것이 원인.

그런데 meta tag는 무엇인가?

> metadata는 데이터를 설명하는 데이터이다.

HTML문서의head태그 안에서 사용한다.


```html
<head>
	<meta charset="utf-8">
	<title>Daum</title>
	<meta property="og:url" content="https://www.daum.net/">
	<meta property="og:type" content="website">
	<meta property="og:title" content="Daum">
	<meta property="og:image" content="//i1.daumcdn.net/svc/image/U03/common_icon/5587C4E4012FCD0001">
	<meta property="og:description" content="나의 관심 콘텐츠를 가장 즐겁게 볼 수 있는 Daum">
	<meta name="msapplication-task" content="name=Daum;action-uri=https://www.daum.net/;icon-uri=/favicon.ico">
	<meta name="msapplication-task" content="name=미디어다음;action-uri=http://media.daum.net/;icon-uri=/media_favicon.ico">
	<meta name="msapplication-task" content="name=메일;action-uri=http://mail.daum.net;icon-uri=/mail_favicon.ico">
	<meta name="referrer" content="origin">
	<link rel="search" type="application/opensearchdescription+xml" href="//search.daum.net/OpenSearch.xml" title="다음">
</head>
```
[https://www.daum.net](https://www.daum.net) head의 일부이다.
1. `<meta charset="utf-8">` : character encoding 설정 태그. 가장 많이 쓰이는 인코딩 설정이다.

2. og는 [Open Graph Data](http://ogp.me/) 는 Facebook이 웹 사이트에 더 풍부한 메타 데이터를 제공하기 위해 발명한 메타 데이터 프로토콜이다. 페이스북에서 링크를 공유하면 화면에 나타나는 정보를 설정할 수 있다.

3. favicon설정 : 기본적인 Daum favicon과 다음메일, 미디어다음일 때를 따로 설정해주었다. Daum 메인과 메일일 때 파비콘이 바뀌는 걸 확인할 수 있다. ~~미디어다음은 안바뀌는데…?~~

4. > referrer는 문서에서 전송된 요청에 첨부된 HTTP 헤더의 참조자(Referer)를 제어함.

5. [https://developer.mozilla.org/en-US/docs/Web/OpenSearch](https://developer.mozilla.org/en-US/docs/Web/OpenSearch)

\
기사를 클릭해서 head를 확인해 보면 더 많은 meta tag가 추가된 것을 확인 할 수 있다.
```html
<meta property="twitter:image" content="https://t1.daumcdn.net/news/201906/17/NEWS1/20190617174141244inee.jpg">
```
그중 하나인데, twitter로 해당링크를 공유할 때 보여줄 이미지를 지정한다. 이런요소를 다양한 property의 이름으로 설정 할 수 있다.


daum은 반응형 사이트가 아니기 때문에 pc에서 확인한 head에는 viewport가 없다. 휴대폰에서 다음사이트에 접속하여 PC화면으로 보기를 하면 뷰포트가 생략된 페이지가 휴대폰 어떻게 보이는 지 알 수 있다. 뷰포트 설정유무를 한 눈에 확인가능.


```html
<meta content="width=device-width,minimum-scale=1.0" name="viewport">
```
google의 head에 있는 viewport설정.

device-width는 pc의 경우 브라우저의 넓이가 된다.

> 기기 독립적 픽셀과 CSS 픽셀 간에 1:1 관계를 설정하려면 initial-scale=1을 포함한다.



###### reference
* [head 태그에는 무엇이 있을까? HTML의 메타데이터](https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML)
* [\<meta>: 문서-레벨의 메타데이터 요소](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta)
* [뷰포트 설정](https://developers.google.com/web/fundamentals/design-and-ux/responsive/?hl=ko#set-the-viewport)

