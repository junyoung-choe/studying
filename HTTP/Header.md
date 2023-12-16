# Header

HTTP 전송에 필요한 모든 부가정보가 담겨져있다

페이지 렌더링시에 Network 를 보면 하나의 요청에 response 와 request 모두 담겨있고  
두 개의 header 또한 확인이 가능하다  

Body 에는 실제 전송할 실제 데이터가 담겨있다
(ex 바이너이 코드(사진, 미디어), text, Json, form 형식, 쿼리 파라미터)

이러한 데이터 형식도  
Context-Type 으로 적혀있다 (Header 에) + 데이터 길이 + 압축 정보  

표준 언어의 형식도 담겨있다 ! (ex) Ko, en)


요청을 보낼때 협상을 이용하여 요청시 원하는 언어의 요구 정도를 적어놓을수 있다  
응답시 가지고있는 언어중에 가장 요구도가 높은 언어로 데이터를 응답해준다  

전송에는  
단순, 압축, 분할, 범위가 존재하고  
분할은 마지막 데이터에 마지막이라고 표시하고 각 데이터의 length 를 따로 적지 x 
범위는 프론트에서 나 이정도 데이터 전달해줘 하고 사용자 맞춤 데이터를 원하면 그만큼만 보내준다 

또한 request Header 에는 reference 안에 요청을 보내기 시점에 현재 url 을 같이 보낸다 !  
따라서 뒤로가기 버튼시에 해당 url 로 이동한다 ! (그때의 정보도 같이 가지고 가나?) 


Host  
요청할때 사용하며 , 필수 정보이다   
하나의 서버가 여러가지의 도메인을 처리해야 할때 or 하나의 IP 주소에서 여러 도메인이 적용 되어 있을떄 
그래야지 응답시에 요청한 기기나 컴퓨터 핸드폰에 맞게 들어간다 (요청지를 알기 위해)

Location  
응답에 담겨 있으며 있다면 해당 url 로 알아서 브라우저에서 요청해서 들어간다 (URL 바뀐 경우 서버에서 지정)

Allow  
허용 가능한 HTTP 메서드가 담겨있다  

retry-after  
유저 에이전트가 다음 요청을 하기까지 기다려야 하는시간 