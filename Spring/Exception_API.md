# API Exception 
Json 으로 요청이 왔고 Json 으로 응답해주기를 원한다 ! 
-> 즉 오류가 발생했다면 Json 으로 오류의 상태를 넘겨줘야 한다 ! (응답 데이터의 Body 안에)

오류에 따른 HTML 을 랜더링 해주는것은 비교적 간단했으나 (서블릿에서 에러 페이지 재 요청)  
API 는 세부적으로 일어난 오류에 대한 정보를 랜더링 해줘야 하기 때문에 간단하지 않다  

HandlerExceptionResolver 를 사용하면 된다 -> ExceptionResolver 

컨트롤러에서 에러가 발생한다면 (해결 한다고 해도 preHandler 는 호출되지 않는다 ! )

HandlerExceptionResolver 를 상속 받아서 구현하고 config(bean)에 등록하고 사용한다 !

API 오류 처리는 오류 발생시 WAS 에 다시 갔다가 오는것이 아닌 오류를 처리하고 일정의 상태 코드를 내려주는것이다 ! 


직접 HandlerExceptionResolver 를 구현하는건 번거롭다 ! 
-> @ExceptionHandler 를 사용한다 !  
HTML 을 활용한 에러 처리는 BasicErrorController 를 사용하는게 편리했다
컨트롤러도 다 구현되어 있고 우리는 그냥 페이지만 만들면 됬다 !


```java

@RestController
public class ApiExceptionController {
    
    @ResponseStatus(HttpStatus.BAD_REQUEST)
    @ExceptionHanlder(IllegalAccessException.class)
    public ErrorResult illegalExHandler(IllegalAccessException e) {
        log.error("[exceptionHandler] ex", e);
        return new ErrorResult("BAD", e.getMessage());
    }
    
}

```

즉 해당 오류가 발생시에 해당 컨트롤러가 매핑된다 ! 