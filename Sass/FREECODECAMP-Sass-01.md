## FreeCodeCamp - [Sass Challenges](https://learn.freecodecamp.org/front-end-libraries/sass)


### Introduction to the Sass Challenges

```
Sass (Syntactically Awesome Style Sheets) 는 CSS pre-processor로서, 복잡한 작업을 쉽게 할 수 있게하고,
코드의 재활용성을 높여줄 뿐 만 아니라, 코드의 가독성을 높여주어 유지보수를 쉽게 해준다.
```

> [CSS pre-processor란?](https://developer.mozilla.org/ko/docs/Glossary/CSS_preprocessor)
CSS 전처리기는 전처리기의 자신만의 특별한 syntax를 가지고 CSS를 생성하도록 하는 프로그램이다. CSS 전처리기를 사용하기 위해서는, web server에 CSS compiler를 설치해야 한다.


### Store Data with Sass Variables

Sass와 CSS의 가장 큰 차이점은 변수를 사용하는 것. 자바스크립트처럼 변수를 선언하고 데이터를 설정하여 사용한다. javascript에서는 let, const를 사용하지만, Sass에서는 $를 사용함.

```css
<style type='text/sass'>
 $text-color:red;
 .header{
   text-align: center;
 }
 .blog-post, h2 {
   color: $text-color;
 }
</style>
```


### Nest CSS with Sass

Sass를 사용하면 CSS 규칙을 중첩할 수있으므로 스타일시트를 구성하는데 유용함.
큰 규모의 프로젝트일 때, CSS 파일은 길어지고 규칙이 많아진다. 부모엘리먼트 안에 자식엘리먼트 코드를 작성함으로써 코드정리에 용이하다. 

```css
<style type='text/sass'>
 .blog-post {
   h1 {
 	  text-align: center;}
   }
 </style>
```


### Create Reusable CSS with Mixins

Sass에서 mixin은 스타일시트 전체에서 재사용할 수 있는 CSS 선언 그룹. 브라우저에 따른 접두어를 사용해야 할 때, 매우 편리함. :astonished:

```css
@mixin box-shadow($x, $y, $blur, $c){
  -webkit-box-shadow: $x, $y, $blur, $c;
  -moz-box-shadow: $x, $y, $blur, $c;
  -ms-box-shadow: $x, $y, $blur, $c;
  box-shadow: $x, $y, $blur, $c;
}

div {
  @include box-shadow(0px, 0px, 4px, #fff);
}
```


### Use @if and @else to Add Logic To Your Styles

조건문도 사용 가능! :astonished::astonished:

```css
<style type='text/sass'>
 @mixin border-stroke($val){
   @if $val == light {
     border:1px solid black;
   }
   @else if $val == medium {
     border:3px solid black;
   }
   @else if $val == heavy {
     border:6px solid black;
   }
   @else {
     border:none;
   }
 }
 
 #box {
   width: 150px;
   height: 150px;
   background-color: red;
   @include border-stroke(medium);
 } 
</style>
```


###### reference
* [http://www.incodom.kr/Sass](http://www.incodom.kr/Sass)
* [https://heropy.blog/2018/01/31/sass/](https://heropy.blog/2018/01/31/sass/)