## animation - cubic-bezier

[codepen](https://codepen.io/0641031/full/XWXMwEJ)

keyframes과 cubic-bezier 이용하여 뱃지에 움직이는 화살표 만들기!

```css
.badge span{
  transform: translateX(50%);
  // rush라는 keyframes을, 3초동안, 이와 같은 속도의 움직임으로, 무한히 반복. 
  animation: rush 3s cubic-bezier(0.680, -0.550, 0.265, 1.550) infinite;
}
@keyframes rush {
  15% {
    transition-timing-function: cubic-bezier(0.680, -0.550, 0.265, 1.550);
    transform: translateX(100%);
  }
  16% {
    opacity: 0;
    transform: translateX(0%);
  }
  24% {
    opacity: 1;
  }
  25% {
    transition-timing-function: cubic-bezier(0.680, -0.550, 0.265, 1.550);
    transform: translateX(50%);
  }
  60% {
    opacity: 1;
  }
  65% {
    opacity: 0;
  }
  70% {
    opacity: 1;
  }
}
```

* animation에 대한 속성은 예전에 한 번 [정리한 적](https://github.com/0641031/TIL/blob/master/CSS/keyframes.md#animation%EC%86%8D%EC%84%B1)이 있다.
* cubic-bezier는 ease-in, ease-out과 같은 transition-timing-function의 한 값으로, 대상의 움직임에 관련된 설정이다. 
* 시각적으로 확인을 하기 위해 [https://matthewlein.com/tools/ceaser](https://matthewlein.com/tools/ceaser) 방문을 추천.


###### reference
* [https://blog.coderifleman.com/2016/12/30/bezier-curves/](https://blog.coderifleman.com/2016/12/30/bezier-curves/)
