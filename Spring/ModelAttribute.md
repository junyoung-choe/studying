# @ModelAttribute

@modelAttribute 를 사용하는 경우
심지어 ModelAttribute는 클라이언트에서 클래스 이름 그대로 사용한다면 model.addAttribute 도 생략이 가능하다
```java

@Getter
@Setter
public class TestModel {
    private String name;
    private int age;
}

@RestController
public class TestController {
    @GetMapping("/")
    public String getTestPage(@ModelAttribute TestModel testModel) {
        System.out.println("이름 : " + testModel.getName());
        System.out.println("나이 : " + testModel.getAge());
        return "test";
    }
}

```


@RequestParam을 사용하는 경우
```java
@RestController
public class TestController {
    @GetMapping("/")
    public String getTestPage(@RequestParam int id,
                              @RequestParam String name,
                              @RequestParam String email,
                              @RequestParam String phone,
                              Model model) {
        List<User> userList = userService.search(id, name, email, phone);
        model.addAttribute("userList", userList);
        return "test";
    }
}
```
