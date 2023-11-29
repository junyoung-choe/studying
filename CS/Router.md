# Router

라우터들의 경로 정함과 이동은 결국 최단경로 이동과 관련이 있다 ! 

실제 public(외부에서 할당받은 IP) private(공유기에서 나눠주는 IP 들) 

경로를 이동하는 방법 
- RIP
UDP/IP 상에서 동작하는 프로토컬이며 Distance Vector 를 기반으로 한다
- OSPF
Link State 라우팅 알고리즘을 기반하는 프로토컬 
- BGP
Path Vector 라우팅 알고리즘 기반 

TTL 홉을 지나는 횟수 ! 

홉이란 라우터와 라우터간의 이동 ! 

TTL 설정으로 무한히 떠도는걸 방지한다  

