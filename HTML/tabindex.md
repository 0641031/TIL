## tabindex and focus

작업하던 파일 modal 창에 tabindex설정이 되어있었다. 페이지 로딩할 때, 팝업처럼 무조건 처음에 뜨는 창으로, z-index로 제일 위에 있도록 설정이 되어있었는데 tabindex의 역할은 뭘까, 해서 찾아봤다.

---

> 포커스란 웹 페이지에서 어떤 순간에 키보드를 눌렀을 때 반응하는 위치를 결정하는 요소


나야 당연하게 마우스를 사용하니까 퍼블리싱을 하더라도 키보드의 포커스 설정을 해본 적이 거의 없는 것 같은데, 키보드만으로 웹페이지를 탐색하는 경우도 있기 때문에 적절하게 사용하는 것이 중요하다고 한다.

1. input text, button, option 등 인터랙티브 HTML요소는 암시적으로 포커스가 가능함.

2. 단락, div 등 상호작용이 필요하지 않은 요소에는 기본적으로 포커스되지 않도록 되어있다.

3. DOM에서의 위치를 기준으로 탭순서에 자동으로 삽입됨.

4. 그러므로 css로 버튼의 위치를 바꿔도 DOM의 순서가 우선함. 키보드로 버튼을 선택하는 사용자에게 혼란을 줄 수도 있기 때문에 주의해야함.
    > 실수로 탭 순서를 잘못 배치하지 않았는지 확인하는 차원에서, 가끔 페이지를 탭 이동하면서 확인해 보세요. 
    > 그다지 어렵지도 않은 일이니 습관적으로 해보는 것이 좋습니다.

5. tabindex=”-1” 일반적인 탭 순서에서 요소 삭제.

6. 0보다 큰 tabindex를 사용하는 것은 안티패턴. 이미지, 문서 제목 같은 비입력 요소에는 더욱 그렇다. 가능하면 DOM이 논리적인 탭 순서를 제공하도록 코드를 배치하는 게 바람직.
사용자가 상호작용할 수 있는 대상이 아니라면 포커스를 가능하게 할 이유가 없다. 이미지의 경우 적절한 alt 속성을 제공하는 것으로 충분.

#### 모달 및 키보드트랩 

임시 키보드 트랩을 구현하여, 모달이 표시되는 동안만 포커스를 트랩하고, 모달이 닫히면 이전에 포커스를 받았던 항목으로 다시 포커스가 돌아가게. (a링크에서 href속성 없으면 focus안됨.)

> A tabindex="-1" value removes the element from the default navigation flow (i.e., a user cannot tab to it), but it allows it to receive programmatic focus, meaning focus can be set to it from a link or with scripting.** This can be very useful for elements that should not be tabbed to, but that may need to have focus set to them.

tabindex="-1" 값은 기본 탐색 흐름에서 요소를 제거하지만(즉, 사용자가 탭으로 이동할 수 없음) 프로그래밍 포커스를 수신할 수 있으며, 이는 링크나 스크립팅을 통해 포커스를 설정할 수 있음을 의미한다.** 이 방법은 탭으로 표시하지 않아야 하지만 포커스가 설정되어야 하는 요소에 매우 유용할 수 있다.

bootstrap.js의 modal관련 스크립트를 보면, enforceFocus로 모달에 포커스를 하는게 있고, 키보드 포커스를 escape 관련 스크립트에서 사용한다. modal div에 tabindex=”-1”를 하지않으면 키보드포커스가 모달밖으로 갈 수도 있기 때문에 esc로 모달닫기가 안된다. 

modal div에 tabindex=”-1”를 설정하는 것은
> A great example of when this is useful is modals. Modal containers are typically unfocusable elements like \<div> or \<section>. When a modal window is open, we may want to move focus to it so that screen readers will read out its content. But, we don’t want the modal container itself to be able to receive tab focus. This can be achieved using a negative tabindex.

모달창이 열리면, 우리는 스크린 리더가 모달의 컨텐트를 읽어야 하므로 포커스를 모달창으로 옮기고 싶은데, 모달 div창 자체가 탭의 포커스를 받는걸 원하는게 아니므로 -1로 tabindex를 -1를 준다. 그리고 focus를 설정하면 되는데, 
bootstrap의 모달의 경우에는 enforceFocus에서 modal안의 element에 포커스설정을 해주기 때문에 따로 포커스설정을 하지 않아도 된다. modal div에 tabindex 설정이 없으면 모달 창 밖에 포커스가 있으므로 escape 설정도 적용되지 않는다.


###### reference
* [https://developers.google.com/web/fundamentals/accessibility/focus/?hl=ko](https://developers.google.com/web/fundamentals/accessibility/focus/?hl=ko)
* [https://bitsofco.de/how-and-when-to-use-the-tabindex-attribute/](https://bitsofco.de/how-and-when-to-use-the-tabindex-attribute/)
