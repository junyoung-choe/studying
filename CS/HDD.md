# HDD
파일들은 HDD 에 어떻게 저장이 되어있나

HDD 에는 
- Cylinder - 여러 개의 Platter로 구성
- Platter - 여러 개의 track 으로 구성
- Track - 여러 개의 Sector 로 구성
- Sector - 데이터를 저장하는 공간
- Arm - Cylinder의 위치 이동 
- Head - Sector의 데이터를 읽고 쓴다  
  HDD Structure:

              +-------------------------+
              |           Platter 1      |
              | +---------------------+ |
              | | Track 1             | |
              | | +-----------------+ | |
              | | |   Sector 1      | | |
              | | +-----------------+ | |
              | | |   Sector 2      | | |
              | | +-----------------+ | |
              | | |   Sector 3      | | |
              | +---------------------+ |
              |                         |
              | +---------------------+ |
              | | Track 2             | |
              | | +-----------------+ | |
              | | |   Sector 1      | | |
              | | +-----------------+ | |
              | | |   Sector 2      | | |
              | | +-----------------+ | |
              | | |   Sector 3      | | |
              | +---------------------+ |
              +-------------------------+

하나의 sector 에는 4Kb 크기의 데이터가 저장되며 sector 의 크기에 상관없이 일정하다 

디스크 파일 저장 (디스크에 어떻게 저장을 해둘것이냐) 
- Continuous Allocation
디스크의 연속된 빈 블록에 ArrayList 처럼 쭉 저장한다 (파일 크기를 미리 알아야 한다)  
Compaction -> 디스크의 빈공간을 제거하고 뒤에를 끌어 당긴다 -> 비효율적
- Chained Allocation
각 블록을 연결하는 방법 Linked List 처럼 연결해 놓는다 ! (연속된 빈 블록이 필요하지 않다)
Chain 방법의 최대 파일의 크기는 4GB 이다 -> 아쉽다
- Indexed Allocation
Index를 사용하여 파일을 저장하고 파일 크기에 관계없이 편리하게 사용이 가능하다
index 파일 크기 관계없이 계속해서 자리들의 저장이 가능하다 (하나의 인덱스에 1024 개 적을수 있고 그 뒤에 다음 인덱스를 기술해서 끝없이 기술 가능)


디스크 스케줄링 (파일들을 어떻게 읽어서 올것이냐)
그렇다면 필요한 데이터를 찾기위해 track을 어떤 순서대로 찾아가는지에 대한 방법에는 
- fifo
- SSTF
- SCAN
- FSCAN
- Cyclic-Scan
- 4-step-scan
등이 존재한다

