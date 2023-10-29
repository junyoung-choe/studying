# @Value 
@Value 는 설정파일에 설정한 내용을 주입시키는 어노테이션이다
(properties or yml 파일에 설정한 내용을 주입시킨다)
민감한 데이터를 따로 분리하여 수정과 관리에 용이하게 제작한다

@Value 를 사용하는 자바 파일에 반드시 @Component를 기입해야 한다 (빈에 등록이 되어야 스캔을 할수있고 값을 얻어온다)

```java
@Component
public class EncryptionUtil {
    
    @Value("${enc.key}"})
public static String key;
    
}
```
만약 위처럼 static 변수를 사용한다면 key 라는 변수는 spring 로드 전에 값이 생성되기에 설정값이 들어가지 않은 null 상태이다 !

```java
@Component
public class EncryptionUtil {

    public static String key;

    @Value("${enc.key}"})
    public void setKey(String value) {
        key = value;
    }
    
}
```

따라서 static 변수로 사용하거나 설정값에서 추가적인 조작이 필요시에는 생성자를 통해서 값을 받아올수 있다 !
생성자는 빈 주입시에 생성자가 실행되기 때문 ! 