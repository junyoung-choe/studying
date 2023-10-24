# @RequestBody
객체를 이용해 바로 주입도 가능하다 ! or map으로 @RequestBody Map<String, Stinrg> 으로 받아야 한다
```java
// 객체
public class Entity{
	private Long id;
    private String name;
    private String address;
}

// API Controller
@PostMapping("/api/post")
public void requestTest(@RequestBody Entity entity) {
    System.out.println("id = " + entity.id);
    System.out.println("name = " + entity.name);
    System.out.println("address = " + entity.address);
}
```

# @ResponseBody
client 에게 응답을 Json 형식으로 보낸다 (Map 에 담아서) 
```java
@PostMapping("/test")
@ResponseBody
public Map<String, String> Test(Entity entity)
```


SSR 방식에서는 get , post 요청에 상관없이 @RequestParam 으로 값을 받아올 수 있다

하지만 JSON 방식으로 값을 주고 받으려면 Body를 사용해서 주고 받아야 한다 

웹에서 화면전환 없이 이루어지는 동작들은 대부분 비동기 통신으로 진행되고 이때 데이터는 Body에 담아서 보내야 한다.




