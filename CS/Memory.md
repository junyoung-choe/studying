# Memory

그러면 해당 프로그램들을 어떻게 memory 에 올려서 사용할래 ?

Patitioning  
- fixed Patitioning
    - equal-size (8M, 8M, 8M)
    - Unequal-size(4M, 8M, 12M)  
고정된 크기로 메모리를 나눠서 사용한다면 사용되지 못하는 공간이 존재할수 있다.

- Dynamic Patitioning  
필요한 크기 만큼만 동적으로 나누어서 사용하는 방법이다 

메모리에 프로그램 들을 로드하는 방법에는 
First-Fit, Best-Fit, Next-Fit 이 존재한다

메모리에는 항상 운영체제가 차지하고 있는 부분이 존재한다  
운영체제도 하나의 프로그램이다 실행시에 메모리에 할당이 된다 -> 메모리에 할당된 프로그램을 프로세스라고 한다.
프로세서는 → CPU -> 프로세서가 프로세스를 잘 돌아가도록 해준다

이때 프로세서가 많아져서 메모리가 가득찬다면 어떻게 될까? -> Page Fault  
HDD의 일부 공간을 가상 메모리로 사용하여 메모리처럼 사용한다 (Swap Out, Swap In)

프로그램이 실행되기 위해서는 모든 파일이 메모리에 올라와야 하지만  
지역성 -> 모든 기능을 다 사용하지 않기에 잘 쓰지 않는건 가상 메모리에 존재하게  
스레싱 -> page fault 가 자주 발생한다

이러한 페이지 fault 가 적게 발생하기 위해서 사용하는 방법이 존재한다 
- Optional Policy
- Least Recently used (LRU)
- FIFO
- CLOCK 방식



