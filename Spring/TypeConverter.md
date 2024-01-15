# TypeConverter  

@NumberFormat(pattern = "###, ###")  
private Integer number;

@DataTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss")  
private LocalDateTime localDateTime;

요청에서 들어온 타입을 내 입맛대로 변경해서 사용한다 

이 내부 로직에는 타입 컨버터가 존재하고 !   
스프링이 제공하는 기능으로 Json 타입에서 Integer 타입으로 변경하고 응답시에는 다시 반대로 전환한다

즉 ModelAttribute 같은 어노테이션으로 객체로 다 매핑해서 받아오는 로직 중간에는  
모두 TypeConverter 가 필요하다 ! 
