# Filter
서블릿이 제공하는 기능이다  

웹과 관련된 기능에서는 필터나 인터셉터 사용을 하는것이 유용하다 !

필터는 수문장의 개념으로 필터를 거친 후에 서블릿이 호출된다
따라서 필터에서 적절하지 않은 요청을 잘라낸다면 디스패처 서블릿까지 가지않고 종료된다 

필터 체인을 사용해서 여러가지의 필터를 단계적으로 방문할수 있다 

Filter 를 IOC 컨테이너에 담기 위해서 bean 으로 등록해놓아야 한다  

서블릿이 제공하는 기능으로 서블릿 컨테이너가(WAS) 싱글톤으로 필터를 등록한다.

내가 원하는 경로에만 url 로 필터를 등록하고 해당 url 매핑전에 filter 를 반드시 거쳐가게 제작한다.

if 로그인 페이지로 인증을 위해서 redirect 보낼때 현재 요청이 왔던 URL 을 같이 보내줘서  
어떤 페이지를 들어가려고 했는지 기억하고 로그인 후에는 다시 보내줄수도 있다

Intercepter 와의 차이점을 생각하자 
