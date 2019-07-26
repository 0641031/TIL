### scroll-snap

1. [프론트엔드 개발자는 왜 구하기 어렵나요?](https://taegon.kim/archives/4810) 이 글의 일부분을 발췌하여 작성한 포스트를 보고 전문을 보고 싶어서 검색해서 코드쓰는사람님 블로그 들어갔다가 와, 이런게 있구나! 하고 해봤다.
2. 예전에 full height 페이지를 만들려고 하다가 아 분명히 css로만 될 거 같은데… 하다 fullpage.js를 썼었는데... 해당 글..에 있는 나쁜 프론트엔드 개발자의 표본이잖아…?


스크롤바가 생기는 부모에 scroll-snap-type를 지정하고 스크롤되는 요소에는 어디를 기준으로 스크롤을 멈출건지 scroll-snap-align을 설정했다.

```css
.parent {
  overflow-y: scroll;
  height: 100vh;
  scroll-snap-type: y mandatory;
}

section {
  height: 100%;
  scroll-snap-align: start;
}
```

`scroll-snap-type`에서는 스크롤의 방향과 스크롤 허용정도를 설정한다. 허용정도의 기본값은 proximity인데 이를 적용하면 스크롤이 요소의 경계에 가까워질 때만 scroll-snap이 동작하고, mandatory일 때는 항상 동작한다.

`scoll-snap-start`에서는 스크롤을 요소의 어느부분에 멈출건지를 설정한다. section의 높이가 .parent의 높이보다 높을 때, scroll-snap-align을 center로 해야 요소의 가운데서 스크롤이 멈추는 걸 확인할 수 있다.

scroll-snap-type은 IE10이상에서 지원하지만 scroll-snap-align은 지원하지 않는다.


[Codepen](https://codepen.io/0641031/pen/WVGyYq)에서 확인 가능



###### reference
* [https://stackoverflow.com/questions/53416348/css-scroll-snapping-vertical-not-working](https://stackoverflow.com/questions/53416348/css-scroll-snapping-vertical-not-working)
* [https://www.codingfactory.net/10799](https://www.codingfactory.net/10799)
* [https://taegon.kim/archives/9807](https://taegon.kim/archives/9807)
