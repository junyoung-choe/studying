# @RequestEntity
HttpStatus, HttpHeaders, HttpBody
세가지의 정보가 포함되어 있다 

status 에는 서버의 상태를 넘겨준다 (100, 200, 300, 400, 500)

header 에는 응답의 header를 정의한다 

body 에는 보통 객체를 넘긴다 (Json)

+ ResponseBody를 사용하지 않아도 Json 형식으로 보내준다

```java

@RestController
@RequiredArgsConstructor
public class ResponseEntityController {

    private final ResponseEntityService service;

    @GetMapping("/user/{id}")
    public ResponseEntity<MyDto> findByid(@PathVariable Long id) {
        User user = service.getUser();
        MyDto dto = new MyDto();

        HttpHeaders header = new HttpHeaders();
        header.setContentType(new MediaType("application", "json", Charset.forName("UTF-8")));

        dto.setStatus(StatusEnum.OK);
        dto.setData(user);
        dto.setMessage("메세지메세지!");

        return new ResponseEntity<>(dto, header, HttpStatus.OK);
    }
}

```