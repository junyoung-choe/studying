# Exception

자바의 메인 메서드를 직접 실행하는 경우 main 이라는 이름의 쓰레드가 실행된다  
실행 도중에 예외를 잡지 못하고 Main() 까지 예외가 던져지면 예외 정보를 남기고 쓰레드는 종료된다 ! 

웹 어플리케이션 경우에는 사용자의 요청별로 별도의 쓰레드가 할당되고, 서블릿 컨테이너 안에서 실행된다 
try- catch 로 어디서든 잡으면 상관 없지만  

만약 웹 어플리케이션에서 예외를 잡지 못했다면 서블릿 밖으로 예외가 던져진다면 어떻게 될까 ?
-> 서블릿이 자체적으로 오류를 처리한다 ! (WAS) (스프링의 기본 예외처리를 꺼놔야 한다)

WAS 는 기본적으로 오류가 넘어오면 RuntimeError 가 발생했다면 error-page/500 으로 다시 서블릿으로 요청을 보낸다  
-> 해당 컨트롤러는 수신을 받아서 오류 페이지를 로드한다 ! 

이때 어떤 오류가 발생할때 어떤 url 로 매핑할지 설정하기 위해서 ! 
-> DispatchType(에러의 종류) 을 설정하고 , filter 를 이용해서 해당 url 로 매핑이 가능하다   

스프링에서는 기본적으로 이러한 기능을 다 제공한다 ! 

기본 경로가 @RequestMappring("/error")
BasicErrorController라는 스프링 컨트롤러를 자동으로 등록하고 매핑을 진행한다  

즉 스프링 부트가 다 만들어놨고 (컨트롤러, 기본 에러 페이지 등록 ) 에러 나타나면 was 에서 erorr 페이지를 찾으러 간다 (즉 페이지만 만들면 된다)

500, 보다 512 가 우선순위가 높다 ! 

