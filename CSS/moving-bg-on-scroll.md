## moving background image horizontally on scroll

[codepen](https://codepen.io/0641031/pen/XWXMwEJ)

스크롤을 움직이면 가로로 움직이는 배경.


```css
.bg{
  position: absolute;
  left: 50%;
  z-index: -999;
  top: 100px;
}
```

* bg를 제일 아래 레이어에 놓고(z-index) 기본위치를 화면의 중간으로 한다.
* 스크롤을 내리면 왼쪽으로, 올리면 오른쪽으로 움직이게 설정.


```javascript
const moveBgImage = () => {
  const bg = document.querySelector('.bg');
  bg.style.left = 'calc(50% - ' + window.scrollY * 2 + 'px)';
}
```

* header와 마찬가지로 window.scrollY 값을 이용하고 scroll event listener에 해당 함수를 실행함. 
