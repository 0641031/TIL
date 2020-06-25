## display : flex - container

[codepen](https://codepen.io/0641031/full/XWXMwEJ)

`display: flex` 스타일을 선언함으로 바로 아래 속한 요소들의 정렬을 쉽게 제어할 수 있음.

```css
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
```

#### 관련된 속성

1. flex-direction : 속한 아이템들의 방향 설정. 
	* row : 기본값. 왼쪽에서 오른쪽으로 표시.
	* row-reverse : row의 반대. 오른쪽에서 왼쪽.
	* column : 수직. 위에서 아래로.
	* row-column : column의 반대. 아래에서 위로.

2. flex-wrap : 줄바꿈 설정.
	* nowrap : 기본값. 한 줄에 표시. 속한 아이템에 지정한 크기를 무시하고 한 줄로 표시.
	* wrap : 여러줄로 표시.
	* wrap-reverse : wrap의 반대 방향으로 여러줄로 표시.

3. flex-flow : flex-direction과 flex-wrap을 한 번에 설정할 수 있음. 
	```css
	.container {
	  flex-flow: column wrap;
	}
	```

4. justify-content : 가로 정렬 방법.
	* flex-start : 기본값. 시작점부터 정렬. 
	* flex-end : 끝점부터 정렬.
	* center : 가운데 정렬.
	* space-between : 첫번째 요소는 시작점, 마지막 요소는 끝점에 붙이고 아이템 간의 간격을 고르게 정렬.
	* space-around : 모든 요소의 간격을 고르게 정렬.

5. align-content : 세로 정렬 방법. 아이템이 여러줄로 표시될 때만 사용.
	* stretch : 기본값. 컨테이너의 크기만큼 늘림.
	* 나머지는 justify-content와 동일함.

6. align-items : 아이템의 정렬 방법. 아이템이 한 줄일때 사용함. align-content가 기본값(stretch)이어야 함.
	* stretch : 기본값. 컨테이너 크기만큼 아이템을 늘림.
	* flex-start, flex-end, center는 justify-content와 동일.
	* baseline : 문자 기준선에 따라 정렬.


###### reference
* [https://heropy.blog/2018/11/24/css-flexible-box/](https://heropy.blog/2018/11/24/css-flexible-box/)
* [https://developer.mozilla.org/ko/docs/Glossary/Flex](https://developer.mozilla.org/ko/docs/Glossary/Flex)
* [https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
