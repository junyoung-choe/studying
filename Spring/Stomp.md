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

