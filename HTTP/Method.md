# HTTP Method

정적 데이터 조회  
-> 이미지, 정적 텍스트 문서 

동적 데이터 조회  
-> 주로 검색, 게시판 목록에서 정렬 필터(검색어)

HTML Form을 통한 데이터 전송  
-> 회원가입, 상품주문, 데이터 변경  
-> get post만 지원한다

HTTP API를 통한 데이터 전송  
-> 회원가입, 상품주문, 데이터 변경
-> 서버 to 서버, 앱 클라이언트, 웹 클라이언트(Ajax)
-> post, get, put, patch, delete
-> 애매한 상황에서는 post로 다 해결이 가능하다 

ex) post 요청으로 서버에게 회원가입 요청을 보낸다면  
서버에서는 등록된 회원의 PK를 응답으로 100 이라는 ID 를 보내주는 상황을 생각해보자 
-> 요청에 변경된 응답을 보내준다면 이건 Collection 방식이라고 한다

ex) 반대로 클라이언트에서 회원 정보 수정을 한다  
front는 회원의 pk 알고있고 해당 pk를 적어서 요청을 보낸다  
이때 리소스의 경로를 알고있기에 store 방식이라고 한다

url 경로는 같게 유지하고 메소드를 다르게 설계하는 것이 좋은 설계이다 (url 에는 리소스만 적는다)  
이렇게 해결되지 않을때 어쩔수없이 url 로 매핑을 다르게 한다  