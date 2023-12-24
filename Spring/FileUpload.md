# FileUpload
스프링에서는  
MultipartFile 이라는 인터페이스로 멀티파트 파일을 편리하게 지원한다.

``` java 
@Slf4j
@Controller
@RequestMapping("/spring")
public class SpringUploadController {
    @Value("${file.dir}")
    private String fileDir;

    @GetMapping("/upload")
    public String newFile() {
        return "upload-form";
    }

    @PostMapping("/upload")
    public String saveFile(@RequestParam String itemName,
                           @RequestParam MultipartFile file,
                           HttpServletRequest request) throws IOException {
        // request 에서 직접 뽑아서 사용하지 않는다 !
        log.info("request={}", request);

        log.info("itemName={}", itemName);
        log.info("multipartFile={}", file);

        if (!file.isEmpty()) {
            String fullPath = fileDir + file.getOriginalFilename();
            log.info("파일 저장 fullPath={}", fullPath);
            file.transferTo(new File(fullPath));
        }

        return "upload-form";
    }
}
```
```java
 @PostMapping("/items/new")
    public String saveItem(@ModelAttribute ItemForm form, RedirectAttributes redirectAttributes) throws IOException {

        UploadFile attachFile = fileStore.storeFile(form.getAttachFile());
        List<UploadFile> storeImageFiles = fileStore.storeFiles(form.getImageFiles());

        //데이터베이스에 저장
        Item item = new Item();
        item.setItemName(form.getItemName());
        item.setAttachFile(attachFile);
        item.setImageFiles(storeImageFiles);

        itemRepository.save(item);
        redirectAttributes.addAttribute("itemId", item.getId());

        return "redirect:/items/{itemId}";
    }

```

이와같이 Multipart 를 Item 이라는 클래스에 정의하고 ModelAttribute 를 통해서 받을수도 있다 

MultipartFile 주요 메서드
file.getOriginalFilename() : 업로드 파일 명
file.transferTo(...) : 파일 저장



