# @RequestMapping

restcontroller 사용시 GET, POST, PUT, DELETE 등의 메소드 형식이 가능하고

from 형식에서는 주로 post get 방식을 사용한다 

@RequestMapping(value = "/hello", method = RequestMethod.GET)
이러한 형식으로 요청 url 의 매핑을 처리한다

하지만 아래의 방식은 같은 어노테이션의 사용과 코드가 길어지는 문제점이 존재한다

```java

@RestController
public class HelloController {

    @RequestMapping(value = "/hello", method = RequestMethod.GET)
    public String helloGet(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.POST)
    public String helloPost(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.PUT)
    public String helloPut(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.DELETE)
    public String helloDelete(...) {
        ...
    }
}

```

따라서 아래와 같이 명시적인 어노테이션 사용이 가능하다 

```java

@RestController
@RequestMapping(value = "/hello")
public class HelloController {

    @GetMapping()
    public String helloGet(...) {
        ...
    }

    @PostMapping()
    public String helloPost(...) {
        ...
    }

    @PutMapping()
    public String helloPut(...) {
        ...
    }

    @DeleteMapping()
    public String helloDelete(...) {
        ...
    }
}

```

무엇보다 이런식으로 사용한다면 같은 url의 요청에서도 다른 기능 처리가 가능하다 