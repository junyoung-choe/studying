# ArrayList

1. 인덱스를 통한 접근이 가능하다.
2. 중간 삽입시 뒤에있는 인덱스들의 자리가 한칸씩 밀려난다.
3. 배열과 달리 특정 인덱스를 삭제하면 뒤의 인덱스를 가진 요소들이 한 칸 씩 앞으로 당겨진다.
4. 내부는 일반 배열로 이뤄져 있으며, 따라서 많은 양의 중간 인덱스의 삽입 삭제에는 부적합하다.
5. 배열처럼 크기를 지정하지 않아도 되므로 유용하게 사용이 가능하다.

- 지속적인 삽입 삭제에는 적합하지 않다 ! 

``` java
import java.util.ArrayList;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>();
        // add() method
        colors.add("Black");
        colors.add("White");
        // 인덱스 자리를 통해서 삽입이 가능하다
        colors.add(0, "Green");
        colors.add("Red");

        // set() method 0번째 Green은 Bule 로 변경된다
        colors.set(0, "Blue");
        
        System.out.println(colors);
        
        // 삭제시에는 인덱스 or 값으로 삭제가 가능하다.
        colors.remove("White");
        
        // 해당 인덱스의 값을 확인할수도 있다 
        int index = colors.indexOf("Red");
    }
}

```