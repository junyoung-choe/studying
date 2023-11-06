# path
스프링에서는 build path 와 정적 페이지 동적 페이지를 직접 지정해주었다   
스프링 부트에서는 동적 페이지들은 static 파일에 넣어두면 해당 명령은 dispather servlet 이 잡지 않고
클라이언트로부터의 요청이 발생하면 서버에서 추가적인 처리 없이 그대로 전달된다 (이미지, 정적 페이지 등)

1. classpath:/static
2. classpath:/public
3. classpath:/resources/
4. classpath:/META-INF/resources
스프링 부트에서 기본 빌드 path 이다

포트 번호와 기본 빌드 path는 properties 파일에서 지정이 가능하다  
추후에는 REST API 사용으로 이 과정도 대체된다 
