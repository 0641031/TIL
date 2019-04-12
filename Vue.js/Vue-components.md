## [Vue JS 2 - The Complete Guide (incl. Vue Router & Vuex)](https://www.udemy.com/vuejs-2-the-complete-guide/) : Second Course Project - Wonderful Quotes


![Wonderful Quotes](https://i.imgur.com/HvPu0Rh.png)

* Quote 입력 가능
* 해당 Quote를 클릭하면 삭제됨
* 현재 몇 개의 Quote가 있는지 progress bar로 보여줌
* 최대 10개의 Quote 등록 가능

[https://github.com/0641031/VueJS/tree/master/section_10](https://github.com/0641031/VueJS/tree/master/section_10)

---

![section_10](https://i.imgur.com/KaVx12G.png)



* 투명도가 들어간 부분은 components 등록하여 사용함을 나타냄.
* 점선 : 부모에서 자식에게 props로 데이터를 넘겨줌.
* 실선 : 자식 컴포넌트에서 부모로 이벤트($emit) 전달.

---

아주 대충 그리긴 했지만 한 번 그려보니 정리가 좀 되는 것 같다.


1. **NewQuote.vue** : 버튼에 이벤트를 걸어 methods를 호출함.

	```
	methods: {
	  createNew(){
		this.$emit('quoteAdded',this.quote);
		this.quote='';
	  }
	}
	``` 
	처음에 이름이 헷갈렸다. 부모에게 'queteAdded'라는 이름으로 해당 이벤트를 전달하므로 부모 컴포넌트에서
	```
	<app-new-quote @quoteAdded="newQuote"></app-new-quote>
	``` 
	이렇게 받아줘야함. App.vue의 data에 quotes 배열에 전달받은 quote를 추가.
	```
	methods: {
	  newQuote(quote){
     	if(this.quotes.length>=this.maxQuotes){
          return alert("Please delete Quotes first");
     	 } // 10개 넘을 때, alert 해주는 부분.
      	this.quotes.push(quote);
      }
	}
	```

2. **Header.vue** : progress bar에 필요한 데이터를 App.vue에서 전달받아야 하므로 props 사용. App.vue에서 등록한 컴포넌트에서 v-bind로 데이터를 전달.
	```
	<app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
	```
	전달받은 데이터로 progress bar의 너비값을 정해줘야 하므로
	```
	<div class="progress-bar" role="progressbar" aria-valuemin="0" aria-valuemax="100"
	:style="{width: (quoteCount/maxQuotes) * 100 + '%'}">
		{{ quoteCount }} / {{ maxQuotes }}
	</div>
	```
	v-bind로 스타일을 정해줌.

3. **QuoteGrid.vue** : App.vue에서 받은 quotes라는 배열의 데이터를 for문을 통해서 **Quote.vue** 컴포넌트로 하나씩 전달. 이 때 slot를 사용함. ~~사실 이부분은 잘 이해가 안됨~~ 
	```
	<app-quote v-for="(quote,index) in quotes" @click.native="deleteQuote(index)">{{ quote }}</app-quote>
	```
	그리고 해당 quote를 클릭했을 때, 삭제가 되는데 이는 위에 나와 있는 것처럼 부모컴포넌트에 이벤트 전달.
	```
	methods: {
	  deleteQuote(index){
		this.$emit('quoteDelete',index);
	  }
	}
	```
	그럼 부모 컴포넌트에서 'quoteDelete'라는 이름으로 전달받아
	```
	<app-quote-grid :quotes="quotes" @quoteDelete="deleteQuote"></app-quote-grid>
	```
	deleteQuote라는 methods호출하여 quotes라는 배열에서 해당 index를 삭제해주면 됨.
	```
	methods: {
	  deleteQuote(index){
	  	this.quotes.splice(index,1);
	  }
	}
 	 ```



수업을 듣다보면 코드만 따라치는것 같을 때도 있는데, 이렇게 한 번 정리하고 나니 이해가 좀 되는 것 같다. 구글링하면 정말 많은 블로그들이 나오는데 좋은 블로그를 만날 때마다 정말 어디 계신지 여쭙고 절이라도 하고 싶은 심정... :clap:


###### reference
* [http://jeonghwan-kim.github.io/vue/2017/03/27/vue.html](http://jeonghwan-kim.github.io/vue/2017/03/27/vue.html)
* [https://joshua1988.github.io/web-development/vuejs/common-error-cases/](https://joshua1988.github.io/web-development/vuejs/common-error-cases/)
* [https://m.blog.naver.com/PostView.nhn?blogId=jjoommnn&logNo=221087514101&proxyReferer=https%3A%2F%2Fwww.google.com%2F](https://m.blog.naver.com/PostView.nhn?blogId=jjoommnn&logNo=221087514101&proxyReferer=https%3A%2F%2Fwww.google.com%2F)
