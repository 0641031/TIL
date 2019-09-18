#### 1. 브라우저란?

- 소비자가 선택한 자원(URL)을 서버에 요청하고, 요청받은 정보를 서버에서 응답하면 그것을 화면에 보여준다.

#### 2. 브라우저의 구조

![Web-Browser-Structure](https://miro.medium.com/max/1152/1*aDQUwsijfEQa6vkhY91N3w.png)

- UI : 소비자가 조작 가능한 영역. 주소창, 뒤로가기 버튼, 즐겨찾기 등등.
- 브라우저 엔진 : UI와 렌더링 엔진 동작 제어
- 렌더링 엔진 : 소비자의 요청을 화면에 표시 ( IE - Trident, Chrome - Webkit, Blink, Safari - Webkit, FireFox - Gecko...)
- 네트워킹 : HTTP요청과 같은 네트워크 호출을 위해서 필요한 부분.
- UI 백엔드 : OS 사용자 인터페이스 방법을 활용하여, 기본적인 위젯을 그림. (OS마다 콤보박스나, 경고창의 모양이 다른것)
- JS엔진 / 인터프리터 : 자바스크립트를 해석하고 실행
- 데이터 저장소 : Local Storage , Indexed DB, 쿠키 등 브라우저 메모리를 활용하여 저장하는 영역.

#### 3. 브라우저의 렌더링 과정

- 브라우저의 렌더링 엔진 : 브라우저의 렌더링이란 서버에서 받은 HTML, CSS, Javascript 등을 변환해서 화면에 픽셀단위로 나타내는 과정을 말한다. 이를 실행하는 게 렌더링 엔진.

    (DOM 생성 → CSSOM 생성 → Render Tree (DOM+CSSOM) 생성 → Render Tree 배치 → Render Tree 그리기)

- 렌더링 과정
    1. DOM의 생성 : Conversion (HTML를 원시 바이트 형태, 보통 8KB 단위로 서버에서 받아와서 해당 파일의 인코딩에 따라 문자로 변환한다.) → Tokenizing (브라우저가 변환된 문자열을 HTML5 표준에 따라 고유 토큰으로 변환한다.) → Lexing (이 토큰들을 다시 각각의 특성과 규칙에 정의한 객체노드로 변환한다.) → DOM생성 (HTML마크업이 여러 태그 간의 관계를 나타내기 때문에 DOM트리 구조를 가진다. DOM트리는 문서 마크업의 속성과 관계를 포함하지만, 렌더링 될 때 표시되는 모습은 CSSOM이 관여함.)
    2. CSSOM 생성 : DOM 생성의 과정을 똑같이 CSS에 반복하여 브라우저가 이해하고 처리할 수 있는 형식으로 변환된다. CSSOM도 트리구조를 가지는데, 하향식으로 규칙을 적용하기 떄문. 최종 스타일을 확정할 때, 해당 노드에 가장 일반적인 규칙으로 시작한 후에, 구체적인 규칙을 적용함.
    3. Render Tree(DOM, CSSOM) 생성 / attachment : DOM트리에서 시작해서, 페이지에 표시되는 각각의 노드에 일치하는 CSSOM규칙을 찾아 붙인다. 이때는 가시적인 노드만 포함된다. 메타태그나, 스크립트 태그나 `display : none` 등으로 스타일이 지정된 노드는 제외된다. `visibility : hidden` 은 스타일이 적용된 노드는 보이지는 않지만 공간을 차지하므로, 렌더링 트리에 포함된다. 비시각적 요소인 head 또한 렌더트리에 포함되지 않음.
    4. Render Tree 배치 / layout or reflow: 브라우저가 화면에 그리기 전에, 해당 노드들을 정확한 위치와 크기로 나타내기 위해서 계산하는 과정. 모든 상대적인 값(%, em, rem)은 절대적인 값(px)으로 변환된다. 
    5. Render Tree 그리기 : 렌더링 트리의 각 노드를 화면의 픽셀로 나타내는 작업.

- 렌더링 엔진은 가능하면 빠르게 내용을 표시하는데, 모든 HTML을 파싱(DOM트리 생성 전) 할 때까지 기다리지 않고 배치와 그리기 과정을 시작한다.
- HTML파서는 script 태그를 만나면 자바스크립트 코드를 실행하기 위해 DOM 생성 프로세스를 중지하고 자바스크립트 엔진으로 제어권한을 넘긴다. 실행이 완료되면 다시 HTML 파서로 제어 권한을 넘겨서 브라우저가 중지했던 시점부터 DOM 생성을 재개한다. 스크립트 태그의 위치에 따라 블로킹이 발생하여 DOM 생성이 지연될 수 있기 때문에 스크립트 태그의 위치가 중요함. → body태그의 가장 아래에 자바스크립트를 위치하는게 좋음. (페이지 로딩 시간이 단축되고, DOM이 완성되지 않은 상태에서 자바스크립트가 DOM을 조작하면 에러 발생하므로)


###### reference
* [https://janghanboram.github.io/2018/06/06/browser-rendering/](https://janghanboram.github.io/2018/06/06/browser-rendering/)
* [https://d2.naver.com/helloworld/59361](https://d2.naver.com/helloworld/59361)
* [https://poiemaweb.com/js-browser](https://poiemaweb.com/js-browser)
