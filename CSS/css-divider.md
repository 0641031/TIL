## css - divider


![drawing dividers using css](https://i.imgur.com/bWjgcfZ.png)

위와 같은 divider를 css로 그리기.

```html
<h2 class="background"><span>Line-behind title left</span></h2>
<h2 class="background text-center"><span>Line-behind title center</span></h2>
```

```css
h2.background {
    position: relative;
    z-index: 1;     
}
h2.background span {
    background: #fff;
    padding: 0 15px;
}
h2.background::before {
    border-top: 2px solid #dfdfdf;
    content: "";
    margin: 0 auto;
    position: absolute;
    top: 50%;
    left: 0;
    width: 95%;
    z-index: -1; 
}
h2.text-center{
    text-align:center
}
```


* `css selector::before`로 간단하게 그릴 수 있다.
* 텍스트를 span태그로 감싸고 배경화면 색을 주고, before와 span에 z-index로 우선순위를 설정하면 된다.
* 텍스트 양 옆으로 간격을 만들기 위해서는 span태그에 padding을 주면 됨.

<sub>css를 사용하다보면 보이는대로 그리려고 하면 안되는 것 같다. 텍스트 양옆으로 선이 있다고 선 두 개를 그리려고 하는 발상으로는 위와 같은 코드를 쓸 수 없다. 
발상 자체가 안되면 되게 좌절하고 이 길이 내 길이 아닌거 같고 엄청 땅파기도 하는데 확실한 건, 하다보면 는다. 그러니까 많이 하도록 하면 된다.</sub>

###### reference
* [https://codepen.io/ericrasch/pen/Irlpm](https://codepen.io/ericrasch/pen/Irlpm)
