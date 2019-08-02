## css에서 사용하는 단위 : rem, em

em을 rem으로 착각하고 사용하다가 폰트크기 이상한데…? 하고 검색해보고 알게 된 차이점을 정리해보자.

### rem
크기의 기준이 최상위요소(html)가 된다. html의 font-size를 설정하지 않았을 경우, 기본값은 16px이지만 브라우저 설정에서 사용자가 다른 값을 설정한 경우에는 바뀔 수 있다.

### em
해당 요소의 폰트크기가 기준이 된다. 상위 요소가 기준이 된다고 생각했는데, 이는 자동으로 상위요소의 폰트크기를 상속하기 때문에 했던 착각이었다.

```html
<body>
    <div class="rem">
            <h3></h3>
    </div>
    <div class="em">
            <h3></h3>
    </div>
</body>
```

```css
body{
  font-size:14px;
}
div.rem{
  font-size:1.5rem;
}
div.em{
  font-size:1.5em;
}
div.rem > h3{
  font-size:2rem;
}
div.em > h3{
  font-size:2em;
}
```

[https://codepen.io/0641031/pen/VopWwp](https://codepen.io/0641031/pen/VopWwp) 여기서 확인가능.

body에 `font-size:14px` 를 주고 div에 각각 font-size를 1.5rem, 1.5em 으로 설정했다.

크롬 개발자도구에서 styles탭 옆에 있는 computed탭에서 계산된 사이즈를 확인할 수 있는데,

| selector  | font-size   |
|---|---|
|  div.rem | 24px (16px * 1.5)  |
|  div.em  | 21px (14px * 1.5)  |

h3태그의 경우는 각각 2rem, 2em으로 설정했는데

| selector  | font-size   |
|---|---|
|  div.rem > h3 | 32px(16px * 2) |
|  div.em > h3  | 42px(21px * 2)  |

가 된다. h3의 부모인 div의 사이즈를 상속하기 때문에 기준이 21px가 됨.

###### reference
* [https://webdesign.tutsplus.com/ko/tutorials/comprehensive-guide-when-to-use-em-vs-rem--cms-23984](https://webdesign.tutsplus.com/ko/tutorials/comprehensive-guide-when-to-use-em-vs-rem--cms-23984)
