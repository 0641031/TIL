### @keyframes

* animation효과의 프레임 설정하는 속성.
* 영상 편집에서 도형의 이동을 표현할 때, 타임라인에 처음의 형태와 마지막의 형태를 설정해 주는 것과 비슷함.

```css
.circle{
  width:200px;
  height:200px;
  margin:0 auto;
  background-color:skyblue;
  animation: circle-to-square 2s 2s infinite alternate;
}

@keyframes circle-to-square{
  from{
    border-radius:0;
  }
  to{
    border-radius:50%;
    background-color:#ccc;
  }
}
```

↑ [확인](https://codepen.io/0641031/pen/MWYYgjL)

#### animation속성

1. animation-name: keyframes의 이름. 위의 코드에선 `circle-to-square`
2. animation-duration: 0s. 애니메이션이 진행되는 시간.
3. animation-timing-function: ease. 애니메이션 속도 옵션. 움직임을 확인해 볼 수 있는 [페이지](https://matthewlein.com/tools/ceaser)
4. animation-delay: 0s. 애니메이션 시작 전 지연시간. 
5. animation-iteration-count: 1. 반복횟수. 계속 반복하려면 infinite.
6. animation-direction: normal. 루프 방향. 위의 예에서 사각형이 원이 되었다가 반복하는데 alternate라는 옵션으로 인해서 루프의 방향을 사각형 → 원 → 사각형, 이 되어 이를 반복함.


#### 다양한 브라우저에서 잘 동작하도록 Vendor Prefixes를 붙여줘야 함

```
.circle{
  -webkit-animation: circle-to-square 2s 2s infinite alternate;
  -moz-animation: circle-to-square 2s 2s infinite alternate;
  -ms-animation: circle-to-square 2s 2s infinite alternate;
  -o-animation: circle-to-square 2s 2s infinite alternate;
  animation: circle-to-square 2s 2s infinite alternate;
}

@-webkit-keyframes circle-to-square{ /* */ }
@-moz-keyframes circle-to-square{ /* */ }
@-ms-keyframes circle-to-square{ /* */ }
@-o-keyframes circle-to-square{ /* */ }
@keyframes circle-to-square{ /* */ }
```

하나의 엘리먼트의 여러가지의 애니메이션을 추가할 때는 쉼표로 구분하여 추가하면 됨.
사각형에서 원으로 변하면서 회전하는 도형을 그리고 싶다면, rotate라는 keyframes을 설정하고

```
.circle{
  animation: circle-to-square 2s 2s infinite alternate, rotate 2s 2s infinite alternate;
}
```

추가하면 됨.


###### reference
* [https://developer.mozilla.org/ko/docs/Web/CSS/@keyframes](https://developer.mozilla.org/ko/docs/Web/CSS/@keyframes)
* [https://webdesign.tutsplus.com/ko/tutorials/a-beginners-introduction-to-css-animation--cms-21068](https://webdesign.tutsplus.com/ko/tutorials/a-beginners-introduction-to-css-animation--cms-21068)
* [https://developer.mozilla.org/ko/docs/Web/CSS/animation](https://developer.mozilla.org/ko/docs/Web/CSS/animation)
