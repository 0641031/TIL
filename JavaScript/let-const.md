### let, const

#### var

- 중복선언을 허용한다.

    ```javascript
    var test = "var";
    var test = "var2";
    
    const test2 = "const";
    const test2 = "const2";
    // SyntaxError: redeclaration of const test2
    ```

- function scope를 갖는다. 그러므로 함수 외부에서 선언된 변수는 모두 전역변수이다.
- var 키워드를 생략하여 변수선언이 가능하다.

#### let, const

- block-level scope : 함수, if문, for문, while문 등 모든 코드 블록 내에서만 유효하다.
    ```javascript
    for(var i = 0; i < 3; i++){}
    console.log(i) // 3
    
    for(let j = 0; j < 3; j++){}
    console.log(j) // ReferenceError: j is not defined
    ```

- 중복 선언할 수 없다.
- Hoisting : var 키워드로 선언된 변수는 호이스팅에 따라 브라우저가 자바스크립트를 해석할 때, 맨 위로 끌어 올려진다. 변수는 3단계에 걸쳐 생성된다.
    1. 선언 단계 : 실행 컨텍스트의 변수 객체에 등록. 스코프가 참조하는 대상.
    2. 초기화 단계 : 변수를 위한 공간을 메모리에 확보. 이 단계에 undefined로 초기화.
    3. 할당 단계 : undefined로 초기화 된 변수에 실제 값을 할당.
    - var 키워드를 사용하면 선언과 초기화 단계가 한번에 이루어진다.
         ```javascript
        console.log(foo);
        var foo;
        // undefined
        ```

    - let의 경우는 선언 단계와 초기화 단계가 분리되어 진행된다. 초기화 이전에 변수에 접근하려고 하면 참조 에러가 발생한다. ⇒ 일시적 사각지대라고 부른다.
        ```javascript
        console.log(foo);
        let foo;
        // ReferenceError: can't access lexical declaration `foo' before initialization
        ```

- let과 const의 차이점
    1. let은 재할당이 가능하나 const는 재할당이 금지된다.
    2. const는 반드시 선언과 동시에 할당이 이루어져야 한다.
        ```javascript
        const foo;
        // SyntaxError: missing = in const declaration
        ```
    3. const에 객체를 할당한 경우, 객체의 내용은 변경할 수 있다. 객체 타입 변수에 할당된 주소값을 변경하여야 되지 않는다면 const를 사용하는게 좋다.

- 변수 선언에는 기본적으로 const를 사용하고 let은 재할당이 필요한 경우에 한정해 사용하는 것이 좋다.


###### reference
* [https://poiemaweb.com/es6-block-scope](https://poiemaweb.com/es6-block-scope)
* [https://velog.io/@marcus/2019-02-10-1702-작성됨](https://velog.io/@marcus/2019-02-10-1702-%EC%9E%91%EC%84%B1%EB%90%A8)