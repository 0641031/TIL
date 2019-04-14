## [Vue JS 2 - The Complete Guide (incl. Vue Router & Vuex)](https://www.udemy.com/vuejs-2-the-complete-guide/) : Handling User Input with Forms - Assignment


![Vue Forms](https://i.imgur.com/ayX7rL3.png)

* Edit the Example from above and create a custom "Full Name" Control which still holds the First Name and Last Name Input Field


---

![section_11](https://i.imgur.com/FegYv2J.png)



1. firstname과 lastname을 각각 입력받는 fullname 컴포넌트를 만들라는 거는데 난 Quote에서 했던 것처럼 컴포넌트에서 입력받은 값을 이벤트로 전달한다고 생각했다.

	```
	<input type="text" id="name" class="form-control"
   		 v-model="name" @keyup="changeName">
	``` 

	그리고 input에서 keyup이벤트로 해당 값을 전달했다.

	```
	changeName(){
   	  this.$emit("changeName",this.name);
    }
	``` 
	이렇게 하면 App.vue에서도 firstname, lastname 따로 전달받기 때문에 중복되는 코드가 많아진다.


2. 풀이에서는, 방향이 다르다. App.vue에서 fullname을 자식 컴포넌트로 전달하여 props로 받아 string을 공백을 기준으로 배열로 나누어서 다룬다. 이 때, computed를 사용하는데 배울 당시에 전혀 이해를 하지 못하다가 김정환님 블로그 보고 이해했다… :thumbsup: 

	```
	computed:{
   	  firstname(){
   		return this.value.split(" ")[0];
   	  },
   	  lastname(){
   		return this.value.split(" ")[1];
   	  }
   	}
	```
	한 번 전달된 내용에 변경사항이 없을 경우 methods처럼 매번 호출 할 필요없이 저장된 캐쉬값을 반환하면 되기 때문에 computed를 쓴 것 같다. 그런데 App.vue에서 기본 값으로 공백이 있는 string을 전달하지 않으면 undefined가 출력된다. ~~괜찮은 방법인가...?~~

	







###### reference
* [http://jeonghwan-kim.github.io/vue/2017/03/27/vue.html](http://jeonghwan-kim.github.io/vue/2017/03/27/vue.html)
