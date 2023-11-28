# 네트워크 7계층

#### 1. 물리 계층 (Physical Layer) - bit
비트를 전송


#### 2. 데이터 링크 계층 (Data Link Layer) - Frame
프레임 단위로 데이터 전송 및 오류 제어  
MAC

#### 3. 네트워크 계층 (Network Layer) - Packet
패킷의 경로 설정 및 라우팅  
IP

#### 4. 전송 계층 (Transport Layer) - Segment
에러 검출 및 복구, 흐름 제어, 신뢰성 있는 통신  
TCP, UDP

#### 5. 세션 계층 (Session Layer) - Data Message
세션 설정, 유지, 종료

#### 6. 표현 계층 (Presentation Layer) - Data Message
데이터의 형식 변환, 암호화, 압축

#### 7. 응용 계층 (Application Layer) - Data Message
최종 사용자와 네트워크 간의 상호 작용을 지원  
HTTP, DNS

계층을 나누는 이유는 유지 보수 측면에서 역할이 확실하기 때문이다 
응집도 -> A 기능을 하기위한 코드들이 잘 모여있는지  
결합도 -> A 기능과 B 기능이 얼마나 얽혀있나  

Protocal -> 절차를 포함한 통신 규약 

HTTP -> HTML 문서를 주고 받는데 사용하는 프로토컬
TCP -> 전송을 제어하기 위한 프로토컬이며 신뢰성있는 통신을 위해 3-hand-shaking | 통신 종료를 위해 4 핸드 쉐이크를 사용한다  
IP -> 패킷이 네트워크를 통해 목적지에 도착할수 있도록 경로를 지정하기 위한 프로토컬  
MAC -> 하드웨어를 제어하는 계층으로 고유한 식별자를 가지고 있다 

MAC 을 사용하는 이유는 공유기에서 즉 부여받은 하나의 IP 에서 여러가지의 기기중 어떤 기기의 요청인지 구분하기 위함도 있다 !