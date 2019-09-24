### Execution Context : 실행 컨텍스트

hoisting, closure 등에 대하여 검색하다보니 실행 컨텍스트에 대해 먼저 공부해야할 것 같아서... 

- 자바스크립트 코드가 실행되고 연산되는 범위를 나타내는 추상적인 개념. 실행 가능한 코드가 실행되기 위해 필요한 환경.
    1. 전역 코드 : 베이스가 되는 실행 구역.
    2. Eval 코드 : eval 함수의 실행 컨텍스트. 
    3. 함수 코드 : 함수가 호출 될 때, 해당 함수의 실행 컨텍스트가 생성됨. 
- 자바스크립트 엔진은 코드를 실행하기 위하여 여러가지 정보가 필요하다. (변수, 함수 선언, 변수의 유효범위, this...)
- 코드를 실행하면 실행 컨텍스트 스택이 생성하고 소멸한다.
- 전역코드로 컨트롤이 진입하면 전역 실행 컨텍스트가 생성되고 실행컨테스트 스택에 쌓인다. 전역 실행 컨텍스트는 애플리케이션이 종료될 때까지 유지된다. 함수를 호출하면 직전에 실행된 코드블록의 위로 쌓이고 할 일을 마치면 소멸하는 구조.

- 실행 컨텍스트의 3가지 객체
    1. Variable object : 변수객체. (변수, 매개변수와 인수정보, 함수 선언; 함수 표현식은 제외)  전역 코드 실행시 생성되는 전역 컨텍스트와 함수를 실행할 때 생성되는 함수 컨텍스트의 경우 가리키는 객체가 다르다. 함수 컨텍스트의 경우 매개변수가 추가된다. 
    2. Scope Chain : 리스트. 전역 객체와 중첩된 함수의 스코프의 레퍼런스를 차례로 저장. 활성객체를 선두로하여 마지막 리스트는 전역객체를 가리킨다. 객체의 프로퍼티가 아닌 변수를 검색하는 메커니즘. (변수가 아닌 객체의 프로퍼티를 검색하는 매커니즘은 프로토타입 체인) 함수 내에서 변수를 참조하면 첫번째 리스트가 가리키는 활성 객체에 접근하여 변수를 검색하고 실패하면 다음 활성 객체를 검색. 이렇게 해서 마지막 전역 객체까지 검색해서 실패하면 에러를 발생시킴.
    3. this value : 함수 호출 패턴에 의해 결정된다. 전역 객체에서는 window를 가리킨다.
    
- 실행 컨텍스트 생성과정
    1. 전역 객체 생성 - 초기 상태의 전역 객체에는 빌트인 객체와 BOM(navigator, location...)와 DOM이 설정되어 있다. 
    2. 전역 코드로 컨트롤이 진입하면 실행 컨텍스트가 생성되고 실행 컨텍스트 스택에 쌓인다.
    3. 실행 컨텍스트를 바탕으로 스코프 체인의 생성과 초기화 - 변수 객체화 실행 - this 결정.
    4. 함수객체는 [[Scopes]] 라는 내부 프로퍼티를 가지게 된다. 자신의 실행환경과 자신을 포함하는 외부 함수의 실행환경과 전역객체를 가리키는데 이때 자신을 포함하는 외부함수의 실행 컨텍스트가 소멸하여도 [[Scopes]]가 가리키는 외부 함수의 실행 환경은 소멸하지 않고 참조할 수 있다. ⇒ 클로저(!) 

        ```javascript
        function foo(){}
        console.dir(foo)
        ```

        로 [[Scopes]]프로퍼티를 확인할 수 있다. (firefox에선 안되고 chrome에서만 나옴)

    5. 함수 선언식은 변수 객체에 함수명을 프로퍼티로 추가하고 함수 객체를 즉시 할당하지만(함수 호이스팅에 따라 브라우저가 자바스크립트를 해석할 때, 맨 위로 끌어 올려짐) 함수 표현식은 일반 변수의 방식을 따른다. 함수 선언식의 경우 선언문 이전에 함수 호출 가능.

        ```javascript
        //함수 선언식
        function foo() { }
              
        //함수 표현식
        var foo = function() {}
        ````

###### reference

* [https://poiemaweb.com/js-execution-context](https://poiemaweb.com/js-execution-context)
* [https://velog.io/@imacoolgirlyo/JS-자바스크립트의-Hoisting-The-Execution-Context-호이스팅-실행-컨텍스트-6bjsmmlmgy](https://velog.io/@imacoolgirlyo/JS-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-Hoisting-The-Execution-Context-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-6bjsmmlmgy)
* [https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/](https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/)