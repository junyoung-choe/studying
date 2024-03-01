# HashMap

- Map 이란 Key, Value 형태로 데이터를 저장하고 관리한다.
- key 는 맵에 오직 유일하게 존재해야 한다.
- Key 값을 해시를 통해서 저장을 해두기 때문에 조회에 빠른 성능을 가지고 있다.


``` java 
import java.util.HashMap;
import java.util.Map;
public class Main {
	public static void main(String[] ar) {
		Map<String,Integer> map=new HashMap();	//<키 자료형, 값 자료형>
		map.put("A", 100);
		map.put("B", 101);
		map.put("C", 102);
		map.put("C", 103); //중복된 key가 들어갈때는 이전 키,값을 지금의 것으로 업데이트
		System.out.println(map);
		System.out.println(map.get("A"));
		System.out.println(map.get("B"));
		System.out.println(map.get("C"));
		
		if(!map.containsKey("A")) {
		    map.put("A", 104);
		}
		
		int = map.getOrDefault("A", -1); 
	}
}
```