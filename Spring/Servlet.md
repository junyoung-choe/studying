# Servlet

WAS  
web Application Server  
HTTP 기반으로 동작한다   
웹 서버 만으로는 사용자에 따른 개인 화면 구성이 불가하다  
WAS 를 통해서 동적 어플리케이션 구성이 가능하다  

WAS 가 너무 많은 역할을 담당했다 ! 
WEB(Web Server) (HTML, CSS, JS, 이미지)  
, WAS  
, DB   
로 구성을 나눴다
-> 정적 리소스가 많이 사용되면 WAS 증설  
or 애플리케이션 리소스가 많이 사용되면 WAS 증설  

정적 리소스만 제공하는 웹 서버는 잘 죽지 않음 애플리케이션 로직이 동작하는 WAS 서버는 잘 죽는다 -> 이때 WEB이 오류 화면 띄울수 있다 


Servlet (HTTP 로직)  
→ 클라이언트의 요청을 처리하고 그 결과를 반환하는 sevlet 클래스의 구현 규칙을 따른 웹 프로그래밍 기술

서블릿이 의미있는 비즈니스 로직을 제외하고 모든 동작을 대신해준다 

HttpServletRequest, HttpServletResponse 요청 응답 정보를 편리하게 사용할수 있다 

서블릿 객체는 싱글톤으로 관리되며 재사용된다 !  
사용자의 요청의 request, reponse 는 계속해서 새로 사용된다 !  
같은 서버에서는 그래도 하나의 서블릿을 이용해서 사용한다 !  

쓰레드 Main 문 실행되는 것이 쓰레드이다 (쓰레드가 서블릿을 호출한다 ! )

CPU 갯수만큼 쓰레드 생성이 가능하기에 멀티 쓰레드를 이용해서 컨텍스트 스위칭을 진행 !  
(이때도 서블릿은 하나이다 쓰레드가 멀티 쓰레드로 여러가지의 request 를 사용해도 서블릿은 한개로 동작 )
이때 쓰레드 풀을 사용한다 

HTTP 요청이 온다면 -> WAS 가 HTTP 요청 형식으로 만들어서 보낸다

톰캣에는 서블릿 컨테이너 기능이 존재한다 !

Spring Boot 는 내장 톰캣을 사용한다

클라이언트의 요청에 의해서 각 사용자 별로 requset, response 가 생성되고  
해당 request 와 response 를 가지고 servlet 을 호출한다

- 스프링부트 관점 servlet
  
WAS (tomcat) 은 서블릿 컨테이너라고 한다 !

여기서 여러 HTTP 요청을 요청 양식에 맞게 변형해주고

REQUEST와 RESPONSE 를 만들어서 dispatherSevlet 에게 전달한다 !

그 이후에 요청을 받은 **DispatcherServlet 은 Handler Mapping를 진행한다 !**

(이 뒤에는 뒤에서 배운 ArgumentResolver 를 사용해서 모든 param 들을 받고 controller 중 가능한걸 매핑한다)

즉 servlet 은 repository 의 로직까지 다 진행한후에 클라이언트에게 return 해줄때까지의 모든 로직에 관여한다 !

but 이게 아니다 !

controller 를 매핑하고 service 를 호출하잖아 ! 여기부터는 서블릿은 대기하거나 차단되는 활동을 한다 !

이때 쓰레드 풀을 이용하면 대기 상태에서 다른 요청을 또 매핑한다 !

이게 서블릿의 주 역할이다 !