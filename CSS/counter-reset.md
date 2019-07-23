### counter-reset

1. list를 사용하는데 list-style로 들어가는 숫자 전,후로 괄호를 넣고 싶었다. 
2. 내용이 길어서 줄바꿈이 되었을 때, 들여쓰기가 되었으면 좋겠다.
3. `list-style-type:decimal`을 사용하고 css에서 `::before` 라던지 되지 않을까, 했지만 숫자를 선택할 수 없기 때문에 불가능.

구글링하다가 stackoverflow에서 찾았다. 

```css
ol{
  counter-reset:item;
  list-style:none;
}
ol li{
  counter-increment:item;
}
ol li::before{
  content: " ("counter(item)") ";
  margin-left:-24px;
}
```

counter-reset, counter-increment란 속성을 사용하는 건데, css에서 변수처럼 counter를 사용할 수가 있다.
counter-reset에서 이름과 시작값을 설정할 수 있는데, 시작값을 따로 설정해주지 않았다면 자동으로 0이 되고,
counter-increment는 설정한 값을 증가시키기 위해 사용한다. 이름과 증가값을 설정할 수 있고, 증가값의 기본값은 1이다.


counter-reset과 counter-increment를 설정하는 건, position:absolute와 position:relative를 사용하는 것과 비슷한 것 같다.
기준이 되는 요소에 reset를 사용하면 된다. 

li안의 p태그에 또 다른 counter를 사용하고 싶다면,


```css
ol{
  counter-reset:item;
  list-style:none;
}
ol li{
  counter-increment:item;
  counter-reset:item2;
}
ol li::before{
  content: " ("counter(item)") ";
  margin-left:-24px;
}
p{
  counter-increment:item2;
}
p::before{
  content: " ("counter(item2)") ";
}
```

이렇게 하면 된다.

[Codepen](https://codepen.io/0641031/pen/bXEmBG)에서도 확인 가능



###### reference
* [https://stackoverflow.com/questions/2558358/how-to-add-brackets-a-to-ordered-list-compatible-in-all-browsers](https://stackoverflow.com/questions/2558358/how-to-add-brackets-a-to-ordered-list-compatible-in-all-browsers)
* [https://www.codingfactory.net/10799](https://www.codingfactory.net/10799)
