## JS, CSS cache

> 예전 프로젝트 할 때, 자바스크립트 파일을 수정해도 적용이 안되서 파일명 뒤에 버전이름을 사용하라고 해서 문제를 해결했던 적은 있는데, 
> 원리를 모르고 그냥 넘어갔다.
>
> img태그에 스트링쿼리 비슷한 게 붙어있어서 무엇을 위한거냐 물어보니 캐쉬때문이라고... img태그에도 쓰는구나!


#### cache의 동작원리

* **캐쉬는 URL을 기준으로 기존에 동일한 URL에 요청한 적이 있었는지를 판단하여 동작한다.** 그러므로 URL을 변경해주면 변경된 파일이 적용되는 아주 간단한 원리!
* `파일명.js?ver=1.0` 이렇게 바꾸어 주는 방법도 있지만 파일의 최종 수정날짜를 붙여주는 방법도 있다.
* java의 경우 [File객체](https://docs.oracle.com/javase/8/docs/api/)에 lastmodified()라는 메소드가 있음.

---

img태그에 대한 캐쉬를 검색하다가 좋은 글 발견! 

캡틴판교님 - [(번역) 웹 개발에서 img 태그 다루는 법](https://joshuajangblog.wordpress.com/tag/%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%BA%90%EC%8B%B1/)

###### reference
* [수정배포된 CSS/JS 파일 캐시 방지](https://www.letmecompile.com/css-js-%ED%8C%8C%EC%9D%BC-%EC%BA%90%EC%8B%9C-%EB%B0%A9%EC%A7%80/)
* [[Front] js/css 파일 캐시 방지 처리](https://yongdev91.tistory.com/1)
* [자바(java) 파일 수정여부 모니터링](https://m.blog.naver.com/PostView.nhn?blogId=seban21&logNo=70113198682&proxyReferer=https%3A%2F%2Fwww.google.com%2F)
