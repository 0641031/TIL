section_14 animation듣다가 과제를 보니 component가 나오길래 다시 section 10 과제로 만들었던 Quote를 만들어 보았다.
그리고 복습을 하며... 삽질을 좀 했다.

당시에 slot부분 이해 못하고 그냥 넘어갔기 때문에 전혀 기억이 나질 않았음. 머릿속에 아예 없었다...
해보고 안되서 검색해보고 아아아 하는거랑 응? 이랑은 전혀 다른데 slot은 보고도 응??? 이었다. :scream:

[컴포넌트가 무엇인가요?](https://kr.vuejs.org/v2/guide/components.html)


---


1. v-bind 말고도 데이터를 전달 할 수는 있지만 동적 데이터의 경우 v-bind 사용해야 함.

2. props 데이터를 전달하면서 유효성 검사가 가능하다.

```
props:{
    //기본값이 100인 숫자타입의 propA가 반드시 필요함.
    propA: {
        type: Number,
	default: 100,
	required: true
    },
    //객체나 배열의 기본값은 함수에서 반환되어야 함.
    propB: {
	type:Object,
	default: function(){
	    return {message : ‘Hello!’}
	}
    },
    //사용자 정의 유효성검사도 가능
    propC: {
	validation: function(value){
	    return value>10
        }
    }
}
```

검증 실패시 콘솔에서 경고.

3. QuoteGrid에서 Quote를 컴포넌트로 사용하는데 여기서 Quote가 루트엘리먼트가 되고 하나의 Quote를 클릭했을 때, 삭제하는 이벤트를 수신해야 하기 때문에 @click.native라고 사용한다.

> 컴포넌트의 루트 엘리먼트에서 네이티브 이벤트를 수신하려는 경우가 있을 수 있습니다.
> 이러한 경우 v-on 에 .native 수식자를 사용할 수 있습니다.

```
<template>
    <div class="row">
   	 <app-quote v-for="(quote,index) in quotes" @click.native="deleteQuote(index)">
   	    {{ quote }}
   	 </app-quote>
    </div>
</template>
```

4. slot

> Vue.js는 현재 웹 컴포넌트 사양 초안을 모델로 한 콘텐츠 배포 API를 구현하며 원본 콘텐츠의 배포판 역할을하기 위해 특수한 \<slot> 엘리먼트를 사용합니다.

컨텐츠 배포를 수월하게 하기 위함. (상단의 코드와 연결됨)

```
<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
        <div class="panel panel-default">
	    <div class="panel-body quote">
	        <slot>There is no quotes.</slot>
	    </div>
        </div>
    </div>
</template>
```
하위 컴포넌트에 \<slot>이 없으면 부모 콘텐츠가 삭제됨. 그리고 <slot>에 삽입할 컨텐츠가 없는 경우 \<slot>사이에 있는 대체 텍스트가 표시됨. (위 코드에서 {{ quote }}를 지우면 발생)

* \<slot>에 name이란 속성을 가질 수 있다. 커스터마이징 하여 여러개의 slot을 사용 할 수 있다.


```
<app-quote v-for="(quote,index) in quotes" @click.native="deleteQuote(index)">
   <p slot="quote">{{ quote }}</p>
   <p slot='writer'>written by 1031</p>
</app-quote>
```

```
<div class="panel-body quote">
    <slot name="quote"></slot>
    <slot name="writer"></slot>
</div>
```


###### reference
* [https://kr.vuejs.org/v2/guide/components.html](https://kr.vuejs.org/v2/guide/components.html)
