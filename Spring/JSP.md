# JSP

(HTML에 자바코드 제작) JSP, typleaf
→ 그래서 동적 페이지이다 !
나중에 JSTL 과 EL을 통해서 자바 코드를 대신한다 !
→ 이게 타임리프랑 아주 유사하다 !

action 이 그냥 save 이면 현재 url에 + 되서 들어간다 → 상대경로
만약 /save 라면 dispatcherServlet 을 통해서 들어간다 → 절대경로

톰캣이 컨트롤러에서 매핑이 안된다면 자동으로 view 파일을 찾았다 !
하지만 만약에 그렇게 호출되기 원하지 않는다면 WEB-INF/views 경로에 두면 찾지 못하게 막는다 !
반대로 가능하게 하고 싶다면 static 파일에 넣는다 !
이건 규칙 !

