# Exception
```java

public Member getMember(Long memberId) {
return memberRepository.findById(memberId).orElseThrow(
() -> new GlobalException(ErrorCode.MEMBER_NOT_FOUND));
}

```

이는 Optional 로 감싸진 엔티티를 반환받을때 사용하는 로직이다 ! 

보통 Optional 을 사용하는 이유는 내가 의존하고 있는 메소드에서 전해준 객체가 Null 인지 판단하라는 의미로 해석할수 있다.

이 과정에서 Optional 내부를 확인하기 위해서는 get() 함수가 필요한데 ! 

orElseThrow() 함수는 Optional 내부가 비어있을때 예외를 발생시키는 함수이다.

이후 예외가 없다면 ! Optional 내부의 객체를 반환한다.



