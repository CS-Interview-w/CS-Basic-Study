# 웹 브라우저에서 Spring 서버로 접속했을 때 일어나는 일

## 원준님이 보내주셨던 세부 주제

### 1. 서버는 Spring Framework, DB 접근은 JDBC / Mybatis 중 선택 View 는 JSP , DB는 Oracle 을 쓴다고 할 때의 시나리오
- (단, 여기서 나는 Spring Framework, DB 접근은 Mybatis, View 는 JSP, DB는 Oracle 을 쓴다고 가정한다.)

#### 웹서버 vs WAS
- 웹 서버 : 클라이언트가 웹 브라우저에서 어떤 페이지 요청을 하면 웹 서버에서 그 요청을 받아 정적 컨텐츠를 제공하는 서버로 단순 HTML 문서, CSS, js, 이미지, 파일 등 즉시 응답 가능한 컨텐츠이다.대표적인 웬서버로 Apache 가 있다.
- WAS : 웹 서버와 웹 컨테이너가 합쳐진 형태로서 웹 서버 단독으로는 처리할 수 없는 데이터베이스의 조회나 다양한 로직 처리가 필요한 동적 컨텐츠를 제공한다. JSP, Servlet 등의 구동 환경을 제공해주기때문에 웹컨테이너, 서블릿 컨테이너등으로도 불린다. 대표적으로 Tomcat 이 있다.
- 웹 서버가 동적 컨텐츠를 요청받으면 WAS에게 해당 요청을 넘겨주고, WAS 에서 처리한 결과를 클라이언트에게 전달해주는 역할을 한다.
- WAS도 정적 컨텐츠를 처리할 수 있으나, WAS만 쓴다면 서버의 부하가 커지기 때문에 정적인 컨텐츠는 웹 서버가 처리한다.

#### Spring 기본 개념
- 오픈 소스 자바 라이브러리로, 웹 애플리케이션과 같은 서버 측 애플리케이션을 자바로 개발할 때 많이 사용된다.
- 스프링에는 다양한 프로젝트가 있으며, 스프링 프레임워크를 중심으로 스프링 클라우드, 스프링 데이터, 스트링 시큐리티, 스프링 배치, 스프링 인티그레이션, 스트링 부트, .. 등등 다양하다.
- 가장 자주 쓰이는 스프링 프레임워크, 스프링 시큐리티, 스트링 부트는 대부분의 애플리케이션에서 사용된다.

#### 스프링 프레임 워크의 대표 기능
- 스프링의 핵심은 스프링 프레임워크이다. 대표 기능은 다음과 같다.
- DI 컨테이너 : 객체의 생성과 관리를 통합해서 사용할 수 있게 해준다.
- 스프링 MVC : HTTP 통신, 화면 관련 프로그램을 효율적으로 만들 수 있게 해준다.
- 스프링 JDBC : 데이터베이스 접근 관련 프로그램을 효율적으로 만들 수 있게 해준다.
- 선언적 트랜잭션 : 데이터베이스의 트랜잭션 제어를 자동으로 해준다.
- 테스트 지원 : 테스트 프로그램 작성을 용이하게 해준다.

#### 스프링 시큐리티, 스프링 부트 간단 설명
- 스프링 시큐리티 : 사용자 인증과 애플리케이션에 대한 사이버 공격을 방지하는 기능을 제공한다. 스프링을 사용하는 애플리케이션에 로그인 기능이 필요한 경우 스프링 시큐리티를 사용한다.
- 스프링 부트 : 스프링을 이용한 애플리케이션 개발의 생산성과 유지 보수성을 높여주는 라이브러리 및 도구

#### ORM의 정의
- 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑(연결)해주는 것을 말한다
- 객체 지향 프로그래밍은 클래스를 사용하고, 관계형 데이터베이스는 테이블을 사용한다. 객체 모델과 관계형 모델 간에 불일치가 존재한다.
- ORM을 통해 객체 간의 관계를 바탕으로 SQL을 자동으로 생성하여 불일치를 해결한다.

#### Mybatis란? 
- MyBatis는 개발자가 작성한 SQL 문을 Java 객체로 자동으로 매핑 시켜주는  프레임워크입니다.
- Java 코드와 SQL 매핑 MyBatis를 사용하면, MyBatis 내부에서 그러한 Boilerplate 코드가 구현되어 있고, MyBatis에서 Java 메소드와 SQL 간에 매핑을 시켜서 개발자는 Java 메소드 선언과 SQL 문만 만들면 MyBatis가 자동으로 그 둘 간을 연결시켜 주게 됩니다. 

#### Mybatis vs JPA
- JPA는 한발 더 나아가서 SQL 문까지 자동으로 생성해 주고, DB 데이터와 Java 객체를 매핑 시켜주는 기술입니다. SQL 문장 작성이 필요 없으니 MyBatis보다 한 단계 더 자동화되어 더 편리함과 반복작업을 없애줍니다.
- JPA의 접근 방식은 이런 ORM(Object-Relational Mapping) 기술을 의미합니다. 즉, 객체와 데이터베이스 간의 매핑 기술을 의미하며, Java 개발자가 좀 더 객체지향 관점에서 개발할 수 있게 하고, 개발을 용이하게 해주어서 DB와 Java 간의 불일치를 해소해 줍니다.
- 복잡한 쿼리와 SQL 제어가 필요한 경우는 MyBatis로 개발할 수 있습니다.
- 간단한 매핑 및 객체 지향적인 접근이 필요한 경우는 JPA가 SQL작성 등의 반복적인 부분을 해결해 줍니다.

#### SSR 과 CSR의 개념과 차이
- CSR(Client Side Rendering) : 렌더링이 클라이언트 쪽에서 일어난다. 
- SSR(Server Side Rendering) : 렌더링이 서버 쪽에서 일어남
- 처음 로딩할 때 CSR 은 HTML, CSS, JS 등을 모두 불러오고, SSR 은 필요한 부분만 불러온다. 그래서 처음 로딩은 CSR 방식이 더 느리다. 그러나, 두번째 로딩부터는 CSR 은 첫 로딩때 구성 코드들을 다운받았기 때문에 빠르고, SSR은 첫 페이지 로딩 과정을 다시 실행하므로 느리다.
- SEO 대응: CSR 은 자바스크립트를 실행시켜 동적으로 컨텐츠가 생성되기 때문에 js 가 실행되어야 metadata가 바뀐다. 그러나 SSR은 애초에 서버 사이드에서 컴파일되어 클라이언트로 넘어오기 때문에 크로러에 대응하기 유용하다.
- 서버 자원 사용 : 매번 서버에 요청하기 때문에 SSR이 서버 자원을 더 많이 사용한다. 또한 CSR 이 서버의 부하를 줄여준다.


### 2. JSP 와 스프링 서버의 상호작용- JSP 와 @Controller, @RestController 와의 상호작용 차이

#### JSP란?
- JSP 란 JavaServer Pages 의 약자이며HTML 코드에 JAVA 코드를 넣어 동적웹페이지를 생성하는 웹어플리케이션 도구
- JSP 가 실행되면 자바 서블릿(Servlet) 으로 변환되며 웹 어플리케이션 서버에서 동작되면서 필요한 기능을 수행하고그렇게 생성된 데이터를 웹페이지와 함께 클라이언트로 응답한다.

#### @Controller vs @RestController
- @Controller : 주로 View를 반환하기 위해 사용. 데이터를 반환해야 할 때는 @ResponseBody를 사용하여 body 에 데이터를 반환한다.
- @RestController : @Controller에 @ResponseBody가 추가된 것.  Json 형태로 객체 데이터를 반환한다. 

#### REST API 란?
- REST API란 REST를 기반으로 만들어진 API
- REST(Representational State Transfer): 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것
- HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE, PATCH 등)를 통해
해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미합니다
- 추후 내용 추가 및 보완 필요

## 원준님이 가르쳐준 내용
#### ![20240820_184537](https://github.com/user-attachments/assets/a5e65832-e751-4fe8-8571-8a888f49a9d3)


#### 웹 브라우저에서 Spring 서버로 접속했을 때 일어나는 일
- 추후 내용 추가 필요

## 참고 URL 과 참고 파트
- 웹서버 vs WAS : https://codechasseur.tistory.com/25
- ORM의 정의 : https://gmlwjd9405.github.io/2019/02/01/orm.html
- Mybatis란?, Mybatis vs JPA : https://www.elancer.co.kr/blog/view?seq=231
- SSR 과 CSR의 개념과 차이: https://hahahoho5915.tistory.com/52
- JSP란? : https://javacpro.tistory.com/43
- @Controller vs @RestController: https://mangkyu.tistory.com/49

## 참고 문헌
- 그림으로 배우는 스프링 6 입문