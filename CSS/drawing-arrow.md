### drawing arrow


화살표 이미지를 사용하는데 되게 단순한 모양이라 css로 만들어서 이미지 사용하는 코드를 없앴다.

border가 어떻게 그려지는지 알면 이해가 아주 쉽다.

1. border의 경계

	![1. border의 경계가 생기는 모양](https://i.imgur.com/FkKnz6e.png)


	```css
	.border{
	  width:50px;
	  height:50px;
	  border-left: 30px solid #547980;
	  border-right: 30px solid #45AdA8;
	  border-bottom: 30px solid #9DE0AD;
	  border-top: 30px solid #E5Fcc2;
	}
	```

	외곽선을 두껍게 그리면 인접하고 있는 부분의 모서리에서부터 대각선이 생기는 걸 확인할 수 있다. 이를 이용해서 화살표를 만드는 것이다.

2. width, height를 0으로 설정

	![2. div의 크기를 0으로 했을 때의 모양](https://i.imgur.com/H1bDEn6.png)

	```css
	.border{
	  width:0px;
	  height:0px;
	  border-left: 50px solid #547980;
	  border-right: 50px solid #45AdA8;
	  border-bottom: 50px solid #9DE0AD;
	  border-top: 50px solid #E5Fcc2;
	}
	```

	div의 크기를 0으로 설정하면 1에서 사각형 안의 흰 공백이 없어지게 된다. 여기서 원하는 화살표의 방향에 따라 필요없는 border의 색을 투명으로 설정해주면 된다.


3. 오른쪽을 향하는 화살표의 경우


	![3. 오른쪽 화살표 1](https://i.imgur.com/GtEMubh.png)


	```css
	.border{
	  width:0px;
	  height:0px;
	  border-left: 50px solid #547980;
	  border-top: 50px solid #45AdA8;
	  border-bottom: 50px solid #9DE0AD;
	}
	```

	 의 그림에서 가장 진한 녹색부분만 필요하기 때문에 `border-right`는 사용하지 않아도 된다. 화살표의 두께는 `border-left`로, 화살표의 높이는 `border-top`과 `border-bottom`의 사이즈로 조절한다. 

4. 화살표!


	![4. 오른쪽 화살표 2](https://i.imgur.com/tExE1bT.png)


	```css
	.border{
	  width:0px;
	  height:0px;
	  border-left: 50px solid #547980;
	  border-top: 50px solid transparent;
	  border-bottom: 50px solid transparent;
	}
	```

[codepen](https://codepen.io/0641031/pen/rNawmxv)

###### reference
* [https://css-tricks.com/snippets/css/css-triangle/](https://css-tricks.com/snippets/css/css-triangle/)