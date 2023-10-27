# @PathVariable
비동기 처리에서 많이 사용하는 방법으로
기존의 URL에 변수명 없이 변수만 넘어오는 상황에서 사용한다.
여러개의 값이 넘어온다면 /로 구분한다

```java
@RestController
public class MemberController { 
    // 기본
    @GetMapping("/member/{name}")
    public String findByName(@PathVariable("name") String name ) {
        return "Name: " + name;
    }
    
    // 여러 개
    @GetMapping("/member/{id}/{name}")
	public String findByNameAndId(@PathVariable("id") String id, @PathVariable("name") String name) {
    	return "ID: " + id + ", name: " + name;
    }
    
}
```