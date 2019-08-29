## robots

1. meta tag를 훑어본 적은 있지만 어떤 태그가 더 있나, 무작위로 사이트의 head를 보다가 `<meta name=”robots”>` 를 만남.
2. github page로 블로그를 만들면 별다른 설정없이 구글 검색결과에 노출이 되고 색인이 생성되기도 한다. github page뿐만 repository도 검색결과에 나온다. 나 아무것도 안했는데…? 왜 이런일이 생기는 거지? 
3. github page로 만든 블로그를 검색결과에 노출하고 싶지 않다면 master말고 다른 브랜치를 사용하면 된다고 했었는데 이유를 알아보자!

---

[How to stop Google indexing my Github repository](https://stackoverflow.com/questions/15844905/how-to-stop-google-indexing-my-github-repository/15987482
)


1. 먼저 검색결과에 노출이 되는데 영향을 주는 건 크롤링을 제어하는 루트디렉토리안에 있는 robots.txt 파일이고, 색인을 제어하는건 head안에 ` <meta name="robots" content=""> ` 라고 한다. (content의 기본값은 index, follow)

    ```
    <meta name="robots" content="nofollow"> `
    ```
    페이지 외부 링크에 대해 크롤링과 같은 추적기능을 사용하지 않도록 검색엔진에 지시하는 역할을 한다. 이는 a링크에서 ` rel="nofollow" ` 처럼 사용할 수도 있다. 


    ```
    <meta name="robots" content="noindex">
    ```
    검색엔진에 해당 페이지를 색인하지 않도록 지정하는 속성. 

    크롤링에 대한 제어는 robots.txt에서 하는데 meta tag 읽기 전에 이 파일을 먼저 읽는다. 

    robots.txt에서 크롤링을 제어하는 방법은 [여기서](https://support.google.com/webmasters/answer/6062596?hl=ko)

    크롤러를 차단하면 페이지에 접근자체가 차단되어 meta tag에도 접근이 불가능하다. 
    그리고 noindex로 색인을 차단해도 결과에 나타날 때가 있는데 이는 검색엔진들이 실제 페이지를 크롤링 하지 않고도 링크만으로 색인이 가능하기 때문이라고. 


2. 색인을 허용하지 않는 가장 좋은 방법은 크롤러를 허용하고 색인을 차단하는 방법이라고 한다. robots.txt파일에서 크롤링을 허용하여 noindex로 설정된 태그에 접근했다면 생성된 색인도 자동으로 삭제한다고 한다.

    github의 [robots.txt](https://github.com/robots.txt)를 보면 여러가지의 User-agent의 설정으로 
    ```
    Allow: /*/*/tree/master
    Allow: /*/*/blob/master
    ```
    라고 되어있는 것을 볼 수 있다. 저 파일을 수정할 수는 없기 때문에, 크롤링을 제어할 수는 없고 github page의 meta태그로 색인은 막을 수 있는 것 같다.


3. robots.txt에 sitemap 파일위치를 등록하면 크롤링하는데 도움을 준다.  
    [https://www.google.com/robots.txt](https://www.google.com/robots.txt) 을 보면 하단에 `Sitemap: https://www.google.com/sitemap.xml`이 있고 해당 파일에서 sitemap도 확인이 가능함.


4. 대부분의 사이트 주소뒤에 robots.txt를 치면 파일을 확인할 수 있는데 daum의 경우
    ```
    User-agent: *
    Disallow: /
    ```
    완전 차단!!

    naver의 경우 
    ```
    User-agent: *
    Disallow: /
    Allow : /$
    ```

    루트페이지만 접근 가능한 설정이라고 한다.

    구글링하면 다음블로그나 네이버블로그의 포스팅이 안나오던 이유가 이거였구나… 

###### reference

* [특정 링크에 rel="nofollow" 사용](https://support.google.com/webmasters/answer/96569)
* [robots.txt 파일과 meta robots 태그의 차이점](http://www.seo-korea.com/robots-txt-%ED%8C%8C%EC%9D%BC%EA%B3%BC-meta-robots-%ED%83%9C%EA%B7%B8%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90/)
* [Stopping index of Github pages](https://stackoverflow.com/questions/32784322/stopping-index-of-github-pages)
* [https://stackoverflow.com/questions/32784322/stopping-index-of-github-pages](
https://stackoverflow.com/questions/32784322/stopping-index-of-github-pages)




