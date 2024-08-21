#### 웹 브라우저에서 HTTP 통신을 통해 스프링 서버로 접속하면
→OSI 7계층을 그대로 따라 서버의 응용 계층 단계에서 스프링이 동작<br>
→Handler Mapping에서 Controller로 가 I/O + 예외처리 실행<br>
→Service에서 비즈니스 로직 수행<br>
→Repository에서 DAO 수행<br>
→DB 연결<br><br>

#### 각 method별 차이
**GET** MyServer url:8080 Index HTML → view 반환하는 Controller 사용<br>
**POST** api bookform → Data 반환하는 Rest Controller 사용<br><br>


#### JSP와 Thymeleaf의 차이
| JSP | th |
| --- | --- | 
| 렌더링 필요(디버깅 힘듦) | 렌더링 불필요(디버깅 쉬움) |
| 서블릿 변환 후 실행 | 그런거 필요 없음 |

<br>

#### 용어 메모
트랜잭션 : 비즈니스적으로 의미있는 작업단위(논리적인 작업단위)<br>
ACID : 트랜잭션 규칙<br>
라우팅 : 데이터 전송 시 최적의 경로 선택 과정<br>
렌더링 : 웹 페이지 화면 구현, SSR과 CSR이 있음
| SSR | CSR |
| --- | --- |
| 서버에서 렌더링 | 클라이언트에서 렌더링 |
| JSP, Thymeleaf | Ajax, Axios |