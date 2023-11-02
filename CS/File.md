# File
window , Mac OS 와 같은 OS 에서 PDF, PNG, JPG 같은 다양한 파일을 인식하고 적절한 아이콘 등을 보여준다

File Singniture  
-> File Magic Number, File checksum 을 참조하여 파일의 내용을 검증하거나 식별하는 데이터이다

File Magic Number  
-> 여러 운영체제 에서 공통으로 사용되며, 간단하고 효과적인 파일 형식을 구별하는 값이다.  
ex) .png 파일은 89 50 4E 47 0D 0A 1A 0A 으로 표현한다

File checksum  
-> 에러를 탐지하기 위한 작은 데이터 크기의 데이버 블록이다  
페리티 비트(홀수 or 짝수)와 CRC(XOR 연산) 같은 방법이 존재한다 

전달 받은 파일을 디코드 해본다면 파일의 형식과 내용을 확인할수 있다 

