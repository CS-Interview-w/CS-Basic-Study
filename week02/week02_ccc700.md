## 프로세스와 스레드
<br>
프로세스 : 실행 중인 프로그램<br><br>
스레드 : 프로세스 내 작업의 단위<br><br>

| 프로세스 데이터 구조 |
| --- | 
| HEAP | 
| STACK |
| DATA | 
| CODE(TEXT) | 

HEAP은 공유자원. 
<br><br>
컨텍스트 스위칭(문맥 교환) : CPU 혹은 코어에서 실행 중인 프로세스나 스레드의 교체작업.
<br><br>
원자적 연산 : 원자처럼 쪼개지듯 여러 단계를 걸친 연산. 이 때 문맥 교환이 끼어들면 결과가 꼬일 수 있다.
<br><br>
프로세스 동기화 : 프로세스 실행 순서를 제어해 원자적 연산의  문제점을 해결하여 데이터 일관성을 유지시킨다.
<br><br>
### 질의응답
Q 싱글톤 쓰는 이유?
<br>
A STW가 길어지는 것을 방지함
<br><br>
Q 싱크로나이즈드 - 모니터란?
<br>
A 모니터 : 각 프로그램/스레드 별 실행 시간 분배
<br><br>
Q 톰캣과 서블릿 리퀘스트의 관계?
<br>
A 톰캣의 역할 중 하나가 서블릿 리퀘스트. 톰캣 자체를 서블릿 리퀘스트 라고도 부름.