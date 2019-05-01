spring frame work를 검색해봤다.

1. [https://gmlwjd9405.github.io/2018/10/26/spring-framework.html](https://gmlwjd9405.github.io/2018/10/26/spring-framework.html)

	와 정리가 너무 잘 되어있다. framework가 무엇인지부터 나와있다. 
	음? design pattern이 뭐지? 들어는 봤는데.


2. [https://dailyworker.github.io/java-design-pattern/](https://dailyworker.github.io/java-design-pattern/)

	step.1에 나온 디자인 패턴의 정의만 읽고 넘어간다. 발생한 문제의 타입에 따라 해결하기 좋은 프로그래밍의 패턴이 있다는 것. 


3. 다시 원래의 블로그로 돌아온다. framework는 여러가지 패턴들의 집합으로 구성 됨.
	framework의 장점은 business logic에만 집중 할 수 있어 생산성이 증대되어있다고 한다. 여기서 말하는 생산성이 정확히 무엇일까? 

	[https://brunch.co.kr/@simmani2013/85](https://brunch.co.kr/@simmani2013/85)

	다른 길로 빠질 수도 있으니 주의해야함.


4. 그리고 이 블로그에서 힌트를 찾았다.

	[https://jins-dev.tistory.com/entry/Spring-Framework-%EC%9D%98-%ED%8A%B9%EC%A7%95%EA%B3%BC-%EB%B2%84%EC%A0%84%EB%B3%84-%EC%A3%BC%EC%9A%94-Feature-%EB%93%A4](https://jins-dev.tistory.com/entry/Spring-Framework-%EC%9D%98-%ED%8A%B9%EC%A7%95%EA%B3%BC-%EB%B2%84%EC%A0%84%EB%B3%84-%EC%A3%BC%EC%9A%94-Feature-%EB%93%A4)

	> 개발 생산성을 위해 지원하는 강력한 기능들에 비해 경량의 프레임워크이고 많은 복잡하거나 귀찮은 부분들
	> (특히 Servlet 처리와 같은 부분들)을 굉장히 효과적으로 프레임워크 단에서 처리해주어
	> 개발자들에게 Business Logic 에만 신경쓸 수 있도록 지원한다. 
	>
	> 출처: https://jins-dev.tistory.com/entry/Spring-Framework-의-특징과-버전별-주요-Feature-들 [Jins' Dev Inside]

	이 부분인데, 이건 학원에서 servlet과 jsp로 프로젝트를 해 본 적도 있고 spring으로 프로젝트 해 본 적이 있어서 알고 있다. 단순하게 첫 번째 프로젝트에서는 각 기능마다 servlet을 만들었고 spring에서는 따로 만들어주던 그 기능을 method로 처리한다.

	이제야 spring framework에 대한 얘기가 나온다.


5. 스프링(Spring)의 개념

	자바 엔터프라이즈 개발을 편하게 해주는 경량급 오픈소스 애플리케이션 프레임워크


6. 자바 엔터프라이즈? 

	> 자바 플랫폼, 엔터프라이즈 에디션(Java Platform, Enterprise Edition; Java EE)은 자바를 이용한 서버측 개발을 위한 플랫폼이다. 
	> Java EE 플랫폼은 PC에서 동작하는 표준 플랫폼인 Java SE에 부가하여, 
	> 웹 애플리케이션 서버에서 동작하는 장애복구 및 분산 멀티티어를 제공하는 자바 소프트웨어의 기능을 추가한 서버를 위한 플랫폼이다. 
	> 이전에는 J2EE라 불리었으나 버전 5.0 이후로 Java EE로 개칭되었다.
	> 이러한 Java EE 스펙에 따라 제품으로 구현한 것을 웹 애플리케이션 서버 또는 WAS라 불린다.


7. 다시 Javs EE로 검색

	* JAVA SE (Java Standard Edition)
	자바 표준 에디션은 가장 기본이 되는 에디션입니다.흔히 자바 언어라고 하는 대부분의 패키지가 포함된 에디션이며
	주요 패키지로는 java.lang.*, java.io.*, java.util.*, java.awt.*, javax.rmi.*, javax.net.* 등이 있습니다.
 
	* JAVA EE (Java Enterprise Edition)
	자바로 구현되는 웹프로그래밍에서 가장 많이 사용되는 JSP, Servlet을 비롯하여, 데이터베이스에 연동하는 JDBC, 그 외에도 JNDI, JTA, EJB 등의 많은 기술들이 포함되어 있습니다.
 
	Java EE는 Java SE의 API에 추가로(lib 디렉토리에 포함되어 있는 JAR파일들)의 차이입니다.

	출처: https://210life.tistory.com/entry/Java-EE와-Java-SE의-차이점 [210 Life]


	참고 : [https://m.blog.naver.com/PostView.nhn?blogId=mk1126sj&logNo=220970553716&proxyReferer=https%3A%2F%2Fwww.google.com%2F](https://m.blog.naver.com/PostView.nhn?blogId=mk1126sj&logNo=220970553716&proxyReferer=https%3A%2F%2Fwww.google.com%2F)


8. [http://www.itworld.co.kr/insight/110817](http://www.itworld.co.kr/insight/110817)

	JDK, JRE, JVM까지 왔다… 다시 처음의 블로그로 돌아간다.


9. POJO기반의…? (Plain Old Java Object)

	[https://limmmee.tistory.com/8](https://limmmee.tistory.com/8)
	[https://m.blog.naver.com/weekamp/186678831](https://m.blog.naver.com/weekamp/186678831)


10. EJB…? (Enterprise Java Beans)

	[https://blog.naver.com/blogpyh/220021874123](https://blog.naver.com/blogpyh/220021874123)
	처음 네 줄 읽고 넘어가야 한다.


spring의 특징에 관한 내용은 곧 강의를 들을 것이기 때문에 가볍게 읽고 넘어갔다.

---

이렇게 약 두 시간이 걸렸다.
머나먼 길이여…

그런데 내가 이걸 설명할 수 있냐 하면 그건 또 아니다. 물론 이렇게 한번 찾아보고 설명할 수 있을 만큼 아는 것도 의심해 볼 일이지만…


![...](https://www.epiphanylaw.com/wp-content/uploads/2017/12/albert.jpg)
