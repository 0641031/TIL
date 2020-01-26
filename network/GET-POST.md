### GET / POST

1. GET
* 정보를 **조회**하기 위한 메서드. (Select)
* url끝에 ? 뒤로 쿼리스트링을 붙여서 데이터를 전달. 데이터는 key=value형식이고 여러개일 경우에는 &로 연결.
* 데이터가 url로 노출되기 때문에 보안상 취약하다.
* 데이터의 크기가 제한된다. ex) HTTP/1.1은 2048자로 제한.
* HTTP 패킷의 Body는 비어있다 => Cotent-type 필드도 HTTP Request Header에 들어가지 않음.
* POST 방식보다 빠르고 캐싱을 사용할 수 있어 브라우저에 요청과 응답이 캐쉬된다. (cache : 클라이언트의 로컬에 리소스의 사본이 저장됨.)

2. POST
* 서버의 값이나 상태를 **변경**하기 위한 용도의 메서드. (Update, Insert, Delete)
* 요청정보를 HTTP 패킷의 Body안에 숨겨서 서버로 전송한다.
* HTTP Request Header의 Content-type에 해당 데이터타입이 표현되며, 전송하고자 하는 데이터 타입을 지정해야함.
* GET 보다는 대용량의 데이터를 전송할 수 있고, GET보다 보안상 안전함.


3. GET은 동일한 요청엔 항상 같은 응답이 와야할 때(=조회) 사용. POST는 서버의 상태를 변경하기 때문에 동일한 요청에도 다른 응답이 올 수 있음.

>그리고 가져오는 곳에 GET을 사용해야 하는 이유가 하나 더 있습니다. 얼마전에도 관련해서 포스팅한 적이 있지만 웹의 핵심이라고 할 수 있는 Link문제입니다. 기본적으로 웹에서 모든 리소스는 Link할 수 있는 URL을 가지고 있어야 합니다.(퍼머링크(permalink)1퍼머링크라면 더 좋겠지만 꼭 퍼머링크가 아니라고 하더라도) 그래야 Link를 할 수 있으니까요. 쉽게 말하면 어떤 페이지를 보고 있을때 다른 사람한테 그 주소를 주기 위해서 주소창의 URL을 복사해서 줄 수 있어야 한다는 것입니다. POST를 할 경우에는 값이 내부적으로 전달되기 때문에 URL만 전달할 수 없죠. 글을 저장하는 경우에는 URL을 제공할 필요가 없기 때문에 POST를 해도 상관이 없는 것이고요.

\[출처] : [https://blog.outsider.ne.kr/312](https://blog.outsider.ne.kr/312)


###### reference
* [https://mangkyu.tistory.com/17](https://mangkyu.tistory.com/17)
* [https://hongsii.github.io/2017/08/02/what-is-the-difference-get-and-post/](https://hongsii.github.io/2017/08/02/what-is-the-difference-get-and-post/)