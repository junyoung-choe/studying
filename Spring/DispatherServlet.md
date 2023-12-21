# DispatherServlet

서블릿은 → 클라이언트에서 요청이 오면 처음에 서블릿이 WAS 에 들어가는데 !

이 과정을 boot의 front controller가 대신해주므로 일반 컨트롤러부터는 서블릿이 필요가 없다 !

그러니 / 만날때만 서블릿을 사용 (front controller 방식) → dispacherServlet

-> 멀티 쓰레드가 가능하게 되는 핵심이다 !

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

이제 서블릿 사용없이 map 으로 넘기고 받으려고 model 사용한다

return 으로 경로없이 파일명만 적으면 view 가 매핑되는건 ! 
이것을 해주는게 view Resolver의 역할이다 !