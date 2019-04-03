## gulp?

> gulp가 뭔지는 모르고 이름만 본 적 있는 상태. 학원에서 프로젝트 때문에 템플릿을 다운 받았을 때, 
> 패키지 안에 gulp파일이 있었는데 eclipse에서 problem에 자꾸 뜨길래 (node.js를 설치하지 않았기 때문이겠지…?) 
> 하나 지워보고 아무 이상 없길래 싹 다 지운 적이 있다. 당시에도 이게 뭐지 하고 검색은 해봤는데 전혀 이해하지 못했다.

* 페이지 속도개선을 위해 이미지 파일을 WebP로 바꾸고, gulp를 통해서 css파일과 js파일을 압축하기로 했다.
* gulp와 grunt에 대한 간단한 설명(이건 task runner라는 거고, 둘은 처리방식이 다르고…)과 함께 gulp파일을 만들었으니 test를 해달라는 요청을 받았다. 


### Task Runner

task runner는 반복되는 작업들을 자동화 하기 위해 사용하는 것이다. 대표적으로 grunt와 gulp가 있다. ([포인트는 webpack이지만 gulp와 grunt의 차이점이 언급된 포스팅](
https://fullest-sway.me/blog/2017/03/29/tool-each/))
test요청과 함께 받은 문서에는 명령어와 간단한 설명밖에 없었는데 [감성프로그래밍님 블로그의 Gulp 입문](https://programmingsummaries.tistory.com/356?category=700959)에 자세하게 설명이 나와있다.
(검색해서 감성 프로그래밍님 블로그 나왔을 때마다 알기 쉽게 설명이 되어있어서 자연스럽게 기억하게 됐다. 최근에는 포스팅을 쉬고 계신 것 같다.) 


### gulpfile.js

1. 자신의 목적에 맞는 플러그인을 npm으로 설치하면 사용할 수 있다. 나는 css파일 압축을 위해서 ‘gulp-minify-css’를 설치했다. 그리고 gulpfile에서 require를 해주어 사용한다.
  ```
  let minify  = require('gulp-minify-css');
  ```
  
2. gulp.task로 임무 설정을 하고
  ```
  gulp.task('cssmin', function () {
      return gulp.src(['css/*.css', '!css/*_min.css'])
          .pipe(minify({keepBreaks: true})) //줄바꿈 유지하기
          .pipe(rename({ //다른 이름으로 저장
              suffix: '_min' //접미어 설정
          }))
          .pipe(gulp.dest('css')); // css라는 폴더에 저장 
  });
  ```
3. 해당 task를 실행해보려면
  ```
  gulp cssmin
  ```
  ‘파일명_min.css’ 라는 압축된 파일이 생성됨.

4. gulp.watch로 특정 폴더를 설정해두면, 수정사항이 있을 경우 해당 임무를 다시 수행한다. 

  ```
  gulp.watch('css/*.css', gulp.series('cssmin''));
  ```

---

git을 조금이라도 써보고 강의를 들어서 이해가 쉬웠기 때문에, node.js에 대해 조금이라도 알았으면 어땠을까 하는 아쉬움이 있다.
위에도 링크했지만 감성프로그래밍님 블로그에 있는 Gulp입문과 함께 올려주신 [github의 gulp-step-by-step](https://github.com/eu81273/gulp-step-by-step)을
참고하면 정말 수월하게 학습이 가능하다고 생각한다. 정말 정말 고맙습니다. :clap::clap:

