# HasText

StringUtils.hasText(String)

Utils 에 존재하는 HasText 를 사용하면 문자열이 비어있지 않은지 확인할 수 있다.

이는 null 이나 공백이 아닌 문자열인지 확인하는 것으로, 한꺼번에 두가지의 체크를 진행한다.

1- if (StringUtils.hasText())

2- if (str != null && !str.equals)

2번처럼 두개의 연산을 적어놓는다면 같은 기능을 하겠지만 코드가 더러워지고 가독성이 떨어진다.

따라서 이러한 메소드를 공부하고 사용하는건 중요하다고 생각한다 !
