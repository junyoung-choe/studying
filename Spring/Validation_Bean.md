# Bean_Validation 

스프링에서 오류들의 정의를 편리하게 정의하고자 만둘어진 어노테이션이다 !

implementation 'org.springframework.boot:spring-boot-starter-web'  
라이브러리를 반드시 import 해야한다   
-> 스프링 부트가 자동으로 Bean Validation 을 인지하고 스프링에 통합한다 

-> 스프링 부트는 자동으로 글로벌 Validation 을 등록한다 (LocalValidatorFactoryBean 을 글로 Validator 로 등록)
이 Validator 는 @NotNull 같은 어노테이션을 보고 검증한다. 이렇게 글로벌 validator 가 등록되어 있기 때문에 @Valid 만 적용하면 된다 ! 

-> 이렇게 글로벌 Validator 가 등록되어 있기 때문에 @Validated 만 적으면 된다 ! 
검증 오류가 발생하면 FieldError, ObjectError를 생성해서 BindingResult 에 담아준다
(글로벌 빈으로 등록해서 @ 어노테이션 보고 에러 잡고, @Validator만 추가하면 에러를 잡아서 해당 객체에 매칭한다 !, 그 매칭은 BindingResult 에 넣어준다 !)

- 검증순서 
@ModelAttribute, @RequestParam 같은 파라미터들을 ArgumentResolver 를 통해서 먼저 매핑을 진행한후에  
객체나 변수와 매칭에 이상이 없다면 그때 BeanValidation 에 적용해서 에러가 있는지 확인한다 (null 값 숫자 범위 등)  

만약 매칭에 실패한다면 (타입이 다르다 int 타입인데 문자가 들어왔다) 그때는 BindingResult 에 담긴다 !  

글로벌 오류를 잡아주는 @ScriptAssert() 가 존재하지만 자바 코드로 직접 잡는것이 더 좋다 !

@Range(min = 1000, max = 1000000, group = {SaveCheck.class, UpdateCheck.class})  
와 같이 사용할 객체만 지정해서 그룹을 지정할수 있지만    

추후에 더 많은 객체와 변수들이 사용되기 때문에 request 객체들을 의도에 맞게 각자 제작해주는 것이 더 좋다 ! 
그렇게 된다면 상품 등록과 상품 수정에서 PK 값이 notNull 로 설정해 에러가 터지는것을 방지할수 있다 ! 

- REST API  
@RequestBody 사용해서 받아오고 앞선 MVC 패턴과 유사하지만 !  
Json 타입은 하나의 String 타입으로 넘어오고 매핑이 되지 않는다면 아예 컨트롤러 까지 들어오지도 않는다 !  
즉 -> BindingResult 에 오류가 들어가지 않는다 !  
이때 터지는 오류는 HttpMessageConverter 단계에서 발생한다 ! 


```java

@PostMapping("/add")
public Object addItem(@RequestBody @Validated ItemSaveFrom, BindingResult bindingResult ) { 
    if(bindingResult.hasError()) {
        return bindingResult.getAllError();
}


```




