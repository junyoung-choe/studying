# @ComponentScan

@Component 가 붙은 파일들을 모두 IOC 컨테이너에 빈으로 등록한다

@Component 는 @Service, @Repository, @Controller, @Configuration이 붙은 클래스 Bean들을 찾아서 Context에 bean등록을 해주는 Annotation이다.

@Repository 에는 추가적으로 SQL 오류를 자바 오류로 보여주는 기능을 탑재하고 있다.