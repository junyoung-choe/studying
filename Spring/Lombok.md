# @Lombok

@Getter, Setter  
private 로 선언된 필드 변수의 값을 지정해주고 가져오는 어노테이션

@AllArgsConstructor  
모든 필드 변수를 파라미터로 받는 생성자를 만들어준다

@NoArgsConstructor   
어떤 파라미터도 받지않는 생성자를 만들어준다 

@RequiredArgsConstructor  
@NonNull 이 붙어있는 변수는 반드시 값이 입력되어야 하는 상황에서 해당 변수들만 파라미터로 받는 생성자 

@ToString  
클래스의 변수들을 기준으로 메소드를 완성시켜준다.

@Data  
@ToString, @EqualsAndHashCode, @Getter, @Setter, @RequiredArgsConstructor를 자동완성 시켜준다.    

@Builder  
생성자 대신 사용이 가능하다 ! 가독성 측면에서 좋다 어떤 값을 먼저 설정하던 상관이 없다
```java
Bag bag = Bag.builder()
		.name("name")
        	.money(1000)
        	.memo("memo")
        	.build();
```

@SLF4J  
Log 를 위한 어노테이션
