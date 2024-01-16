자바를 사용하여 웹페이지를 동적으로 생성하는 서버측 프로그램 혹은 그 사양.



![[img1.daumcdn.png]]

- 클라이언트의 요청에 대해 동적으로 작동
- html을 사용하여 요청에 응답
- [[Thread]] 이용하여 동작
- MVC 패턴에서 Controller로 이용
- HTTP 프로토콜 서비스를 지원하는 javax.servlet.http.HttpServlet 클래스를 상속받는다.
- UDP보다 처리속도가 느리다.
- Html 변경 시 Servlet을 재컴파일해야하는 단점이 있다. 