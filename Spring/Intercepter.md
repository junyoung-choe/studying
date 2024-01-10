# Intecepter  

HTTP 요청 -> WAS -> 필터 -> 서블릿 -> 스프링 인터셉터 -> 컨트롤러

스프링이 제공하는 기능이기에 서블릿 이후가 실행 순서가 된다 !  

인터셉터는 필터의 기능보다 훨신더 정교하고 많은 기능을 가지고 있다 

1. preHandler 컨트롤러 호출 전에 호출된다  
2. postHandler  컨트롤러 호출 후에 호출된다  
3. afterHandler 뷰가 렌더링 된 이후에 호출된다  

if 1번 이후에 에러가 발생한다면 ! -> 3번에서 해당 오류를 받아온다 
즉 3번은 무조권 호출되며 예외 발생시 해당 예외를 기억하고 있다 

MVC 구조에서 특화된 기능을 가지고 있다 !

3개의 함수의 실행 시점이 다 다르기에 response, request 에 계속해서 담아서 보내고 사용해야 한다 

Bean 으로 등록하고 사용한다 