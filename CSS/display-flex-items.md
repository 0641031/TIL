## display : flex - items


#### 관련된 속성

1. order : 아이템 순서 설정. (접근성을 고려하면 사용안할거 같음.)

2. flex : 아이템 너비의 비율 설정.
	* flex-grow : 기본값 0. 증가 비율. 숫자가 클 수록 너비가 넓어짐. 
	* flex-shrink : 기본값 1. 감소 비율. 숫자가 클 수록 너비가 좁아짐.
	* flex-basis : 공간 배분 전 기본 너비. 기본값 auto.

	```css
	.item {
	  /* flex: [flex-grow] [flex-shrink] [flex-basis] */
	  flex: 1 1 10px;
	  /* flex: [flex-grow] [flex-shrink] */
	  flex: 1 1;
	  /* flex: [flex-grow] [flex-basis] */
	  flex: 1 10px;
	}
	```

	* flex-grow를 제외한 나머지 속성은 생략가능.
	* `flex: 1 1;` 처럼 써서 flex-basis를 생략하면 기본값인 auto가 아니라 0이 적용됨.
	* 단위를 쓰면 flex-basis flex-basis가 적용됨.


3. align-self : 교차축(item 방향에 대응하는) 정렬 방법. 
	* auto : 기본값. container의 align-items을 상속.
	* stretch : 컨테이너 크기만큼 아이템을 늘림.
	* flex-start : 시작점부터 정렬. 
	* flex-end : 끝점부터 정렬.
	* center : 가운데 정렬.
	* baseline : 문자 기준선에 따라 정렬.


###### reference
* [https://heropy.blog/2018/11/24/css-flexible-box/](https://heropy.blog/2018/11/24/css-flexible-box/)
* [https://developer.mozilla.org/ko/docs/Glossary/Flex](https://developer.mozilla.org/ko/docs/Glossary/Flex)
* [https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
