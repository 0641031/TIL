## navigator.platform

1. 탭이 여러개인 화면에서 PC로 접속했는지, 모바일로 접속했는지 javascript에서 판단하고 기본탭을 설정해야했다.
2. 애플 모바일디바이스의 경우 추가로 css를 첨부하기 위하여 접속기기를 판별할 때, navigator.platform을 사용해봤다. 
  `/iPad|iPhone|iPod/.test(navigator.platform) `
  
---

* navigator.userAgent와의 차이점
  1. navigator.userAgent 는 브라우저 정보를 문자열로 반환하고, 
  2. navigator.platform은 브라우저가 실행되고 있는 운영체제 정보를 문자열로 반환한다. 

  (mdn문서에는 userAgent가 곧 지원이 중단된다고 나와있다.)

* 모바일로 접속했는지 구분하려는 의도가 다양하기 때문에 경우에 따라서 터치스크린의 사용여부를 기준으로 할 수도 있다. 

* 테스트를 윈도우와 아이폰밖에 못했지만, platform의 경우 userAgent에 비하면 간단한 문자열이 반환된다. 
  
  <sub>아이폰의 경우, IPhone, 윈도우를 사용하고 있는 랩탑의 경우 Win32 라는 문자열이 반환 됨.</sub>

* 외에도 반환할 수 있는 값에는 Linux i686, MacIntel, SunOS, Win16, WinCE 등등이 있다. switch문이나 if문으로 해당문자열을 포함하고 있는지 확인하여 사용하면 될 것 같은데…

* [https://stackoverflow.com/questions/19877924/what-is-the-list-of-possible-values-for-navigator-platform-as-of-today](https://stackoverflow.com/questions/19877924/what-is-the-list-of-possible-values-for-navigator-platform-as-of-today)

  navigator.platform의 반환값 리스트를 확인할 수 있는 게시물인데 Nokia Lumia 1520의 경우 핸드폰인데도 반환값이 Win32이므로 이런 경우에 navigator.platform을 사용하는게 100% 정확하다고는 할 수 없을 거 같다. 

* 비교적 최근에 stackoverflow에 올라온 mobile device를 구분하는 가장 좋은 방법을 묻는 질문인데 

  [https://stackoverflow.com/questions/3514784/what-is-the-best-way-to-detect-a-mobile-device](https://stackoverflow.com/questions/3514784/what-is-the-best-way-to-detect-a-mobile-device)

  userAgent를 사용한 다양한 방법이 답변으로 올라와있고 거기에 UserAgent의 타겟이 계속 움직이기 때문에 사용을 추천하지 않는다는 댓글이 엄청나게 공감을 얻고있다. 그렇다고 뭔가 딱 떨어지는 답변도 없다…


이건 정말 의도에 따라 엄청 다양한 코드가 나올 것 같다. ~~난 일단 navigator.platform 사용했는데 개운하지가 않다...~~ 
계속해서 업데이트 해나가야 할 주제이다.



###### reference
* [https://developer.mozilla.org/en-US/docs/Web/API/NavigatorID/platform](https://developer.mozilla.org/en-US/docs/Web/API/NavigatorID/platform)
* [http://tcpschool.com/javascript/js_bom_navigator](http://tcpschool.com/javascript/js_bom_navigator)
* [https://www.w3schools.com/jsref/prop_nav_platform.asp](https://www.w3schools.com/jsref/prop_nav_platform.asp)
