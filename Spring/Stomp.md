# Stomp
Simple Text Oriented Messaging Protocol  
메시지를 전송하기 위한 프로토콜로 메시지 브로커를와 publisher - subscriber 방식을 사용한다  
STOMP는 HTTP와 비슷하게 frame 기반 프로토콜 command, header, body로 이루어져 있다.

```java 
@Controller
@RequiredArgsConstructor
public class StompChatController {

  private final SimpMessagingTemplate template; //특정 Broker로 메세지를 전달
  
  @MessageMapping(value = "/chat/enter")
  public void enter(ChatMessage message) {
    message.setMessage(message.getWriter() + "님이 채팅방에 참여하였습니다.");
    template.convertAndSend("/sub/chat/room/" + message.getRoomId(), message);
  }

  @MessageMapping(value = "/chat/message")
  public void message(ChatMessage message) {
    template.convertAndSend("/sub/chat/room/" + message.getRoomId(), message);
  }
}
```

```java 
@Controller
@RequiredArgsConstructor
@RequestMapping(value = "/chat")
@Log4j2
public class RoomController {

  private final ChatRoomRepository repository;

  //채팅방 목록 조회
  @GetMapping(value = "/rooms")
  public ModelAndView rooms(){

    log.info("# All Chat Rooms");
    ModelAndView mv = new ModelAndView("chat/rooms");

    mv.addObject("list", repository.findAllRooms());

    return mv;
  }

  //채팅방 개설
  @PostMapping(value = "/room")
  public String create(@RequestParam String name, RedirectAttributes rttr){

    log.info("# Create Chat Room , name: " + name);
    rttr.addFlashAttribute("roomName", repository.createChatRoomDTO(name));
    return "redirect:/chat/rooms";
  }

  //채팅방 조회
  @GetMapping("/room")
  public String getRoom(String roomId, Model model){

    log.info("# get Chat Room, roomID : " + roomId);

    model.addAttribute("room", repository.findRoomById(roomId));

    return "chat/room";
  }
}
```

Stomp

STOMP는 HTTP 에서 모델링되는 Frame 기반 프로토콜이다. Frame은 몇 개의 Text Line으로 지정된 구조인데 첫 번째 라인은 Text이고 이후 Key:Value 형태로 Header의 정보를 포함한다. 다음 빈 라인을 추가하고 Payload가 존재한다. 이 구조를 보면 HTTP 요청과 왜 유사한지 알 수 있다.

COMMAND
header1:value1
header2:value2

Body^@
COMMAND : SEND, SUBSCRIBE를 지시할 수 있다.
header : 기존의 WebSocket으로는 표현이 불가능한 header를 작성할 수 있다.
destination : 이 헤더로 메세지를 보내거나(SEND), 구독(SUBSCRIBE)할 수 있다.
destination는 의도적으로 정보를 불분명하게 정의하였는데, 이는 STOMP 구현체에서 문자열 구문에 따라 직접 의미를 부여하도록 하기위함이다.

따라서 destination 정보는 STOMP 서버 구현체마다 달라질 수 있기 때문에 각 구현체의 스펙을 살펴보아야 한다.

그러나 일반적으로 다음의 형식을 따른다.

"topic/.." --> publish-subscribe (1:N)
"queue/" --> point-to-point (1:1)


다음은 ClientA가 5번 채팅방에 대해 구독을 하는 예시이다.

SUBSCRIBE
destination: /topic/chat/room/5
id: sub-1

다음은 ClientB에서 채팅 메세지를 보내는 예시이다.

SEND
destination: /pub/chat
content-type: application/json

{"chatRoomId": 5, "type": "MESSAGE", "writer": "clientB"} ^@


STOMP 서버는 모든 구독자에게 메세지를 Broadcasting하기 위해 MESSAGE COMMAND를 사용할 수 있다. 서버는 내용을 기반(chatRoomId)으로 메세지를 전송할 broker에 전달한다. (topic을 sub로 보아도 될 것 같다.)

MESSAGE
destination: /topic/chat/room/5
message-id: d4c0d7f6-1
subscription: sub-1

{"chatRoomId": 5, "type": "MESSAGE", "writer": "clientB"} ^@