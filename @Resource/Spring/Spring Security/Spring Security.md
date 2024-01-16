스프링 기반 애플리케이션의 보안을 담당하는 스프링 프레임워크

### Authentication
### Authorization
### Principal
### Credential

기본적으로 세션 - 쿠키 방식을 사용

![[image.png]]

[[AuthenticationFilter]]
[[AuthenticationManager]]
[[AuthenticationProvider]]


### Form login

1. 요청 수신

- 사용자가 form을 통해 로그인 정보가 담긴 Request를 보낸다.

2. 토큰 생성

- AuthenticationFilter가 요청을 받아서 UsernamePasswordAuthenticationToken토큰(인증용 객체)을 생성
- UsernamePasswordAuthenticationToken은 해당 요청을 처리할 수 있는 Provider을 찾는데 사용

3. AuthenticationFilter로 부터 인증용 객체를 전달 받는다.

- Authentication Manager에게 처리 위임
- Authentication Manager는 List형태로 Provider들을 갖고 있다.

4. Token을 처리할 수 있는 Authentication Provider 선택

- 실제 인증을 할 AuthenticationProvider에게 인증용 객체를 다시 전달한다.

5. 인증 절차

- 인증 절차가 시작되면 AuthenticationProvider 인터페이스가 실행되고 DB에 있는 사용자의 정보와 화면에서 입력한 로그인 정보를 비교

6. UserDetailsService의 loadUserByUsername메소드 수행

- AuthenticationProvider 인터페이스에서는 authenticate() 메소드를 오버라이딩 하게 되는데 이 메소드의 파라미터인 인증용 객체로 화면에서 입력한 로그인 정보를 가져올 수 있다.

7. AuthenticationProvider 인터페이스에서 DB에 있는 사용자의 정보를 가져오려면, UserDetailsService 인터페이스를 사용한다.

8. UserDetailsService 인터페이스는 화면에서 입력한 사용자의 username으로 loadUserByUsername() 메소드를 호출하여 DB에 있는 사용자의 정보를 UserDetails 형으로 가져온다. 만약 사용자가 존재하지 않으면 예외를 던진다. 이렇게 DB에서 가져온 이용자의 정보와 화면에서 입력한 로그인 정보를 비교하게 되고, 일치하면 Authentication 참조를 리턴하고, 일치 하지 않으면 예외를 던진다.

9. 인증이 완료되면 사용자 정보를 가진 Authentication 객체를 SecurityContextHolder에 담은 이후 AuthenticationSuccessHandle를 실행한다.(실패시 AuthenticationFailureHandler를 실행한다.)