## shrink header on scroll

[codepen](https://codepen.io/0641031/pen/XWXMwEJ)

스크롤을 내리면 높이가 줄어드는 고정 헤더.


```css
header{
  height: 100px;
  width: 100%;
  line-height: 100px;
  position: fixed;
  top:0;
  transition-duration: .3s;
  transition-timing-function: ease-in-out;
}
.height-80{
  height: 80px;
  line-height: 80px;
  transition-duration: .3s;
  transition-timing-function: ease-in-out;
}
```

* `window.scrollY` : 문서에서 수직으로 얼마나 스크롤 됐는지 픽셀값을 반환. (X explorer 9)
* ↑를 이용하여 높이 조절하는 클래스를 추가하거나 제거하여 제어.
* 자연스럽게 변형되도록 transition 이용.




###### reference
* [https://developer.mozilla.org/ko/docs/Web/API/Window/scrollY](https://developer.mozilla.org/ko/docs/Web/API/Window/scrollY)
* [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)

