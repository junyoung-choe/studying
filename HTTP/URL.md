# URL
1. host  
호스트 명으로 ex) www.google.com 으로 서버로 전달전에 해당 IP 주소를 DNS 에서 검색후 전달한다...
2. Port  
접속 포트로 일반적으로는 생략한다 생략시 http는 80 https는 443 이다 
3. path  
리소스 경로로 일반적으로 rest api 설계시 request mapping 이 되어있는 리소스 이름이다.
4. query  
key = value 형태이며 ? 로 시작하며 &로 추가 기능을 지정할수 있다