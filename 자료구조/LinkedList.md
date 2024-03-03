# LinkedList

1. 단방향 연결 리스트

2. 양방향 연결 리스트

3. 양방향 원형 연결 리스트

boolean add(Object obj) LinkedList의 마지막에 객체를 추가한다. (성공하면 true)

void add(int index, Object element) 지정된 위치(index)에 객체를 저장한다.

Object remove() LinkedList의 첫 번째 요소를 제거

Object remove(int index) 지정된 위치(index)에 있는 객체를 제거한다.

boolean remove(Object obj) 지정된 객체를 제거한다. (성공하면 true)

remove 는 인덱스 접근과 value 의 접근도 가능하다

```java
LinkedList<String> list = new LinkedList<>();
list1.add("10");
list1.add("20");
list1.add("30");
 
list1.set(1, "A"); // index 1번의 데이터를 문자열 "A"로 변경한다.
System.out.println(list1); // // [10, A, 30]
```

add 와 set 의 차이점을 이해하고 넘어가자

그렇다면 왜 Liked List 의 내부 구조를 이해해야 할까?

```java

import java.util.*;
import java.io.*;

// 이 문제는 완전 탐색으로 노드 a 와 b 의 부모 리스트를 다 뽑아놓고 a*b 의 비교로 공통 조상을 찾을수도 있다 ! 
// 노드의 숫자가 많아진다면 부모 노드들을 탐색하는 과정 * 공통조상을 찾는 과정으로 시간 효율이 커진다 ! 
// 따라서 -> 

// LCA 란 이진트리에서 부모와 자식의 관계가 확실하게 주어졌을때 (입력순으로 A 가 B 의 조상이다 )
// 공통 조상을 찾는 알고히즘이다 ! 
// Node 라는 클래스에 해당 노드의 level 과 parent 의 노드 번호를 저장한다
// 문제에서 root 노드가 주어지지 않았다면 ? 
// root 노드를 알아야지 depth ( level ) 을 구할수 있다 ! 
// 입력 a, b 에서 b 를 다 체크한다면 (트리라는 정답이 정해져 있다 )

public class Main
{
    public static class Node {
        int level, parent;
    }
    
    static Node[] nodes;
    static ArrayList<ArrayList<Integer>> arr;
    
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st;
		StringBuffer sb = new StringBuffer();
		
		int T = Integer.parseInt(br.readLine());
		
		for (int tc=1; tc <= T; tc++) {
		    int N = Integer.parseInt(br.readLine());
		    
		    // 링크드 리스트 -> 연결정보 
		    arr = new ArrayList<ArrayList<Integer>>();
		    for(int i=0; i<=N; i++) {
		        arr.add(new ArrayList<Integer>());
		    }
		    
		    // 객체도 초기화가 필요하다 
		    nodes = new Node[N+1];
		    for(int i=0; i<N+1; i++) {
		        nodes[i] = new Node();
		    }
		    
		    // 루트 노드를 찾기위함 
		    boolean findRoot[] = new boolean[N+1];
		    
		    // 트리이기에 N-1 개의 간선이 주어진다 ! 
		    for(int i=0; i<N-1; i++) {
		        st = new StringTokenizer(br.readLine());
		        
		        int a = Integer.parseInt(st.nextToken());
		        int b = Integer.parseInt(st.nextToken());
		        
		        arr.get(a).add(b);
		        findRoot[b] = true;
		        
		        // 노드의 정보에 넣어둔다 
		        nodes[b].parent = a;
		    }
		    
		    // 루트 노드를 찾는다 !
		    int root = 0;
		    for(int i=1; i<=N; i++) {
		        if(!findRoot[i]) {
		            root = i;
		            break;
		        }
		    }
		    
		    // 노드들의 level 을 찾고 저장해둔다 ! 
		    BFS(root);
		    
		  //  for(Node node : nodes) {
		  //      System.out.println(node.level);
		  //  }
		    
		    st = new StringTokenizer(br.readLine());
		    int q1 = Integer.parseInt(st.nextToken());
		    int q2 = Integer.parseInt(st.nextToken());
		    
		    sb.append(LCA(q1, q2) + "\n");
		} 
		System.out.println(sb);
	}
	
	// 조상 자식 관계가 확실하기에 ch 배열이 필요없다 
	public static void BFS(int root) {
	    Queue<Integer> Q = new ArrayDeque<>();
	    int depth = 0;
	    Q.add(root);
	    
	    while(!Q.isEmpty()) {
	        depth++;
	        int size = Q.size();
	        
	        // 하나의 depth
	        for(int i=0; i<size; i++) {
	            
	            int now = Q.poll();
	            nodes[now].level = depth;
	            
	            for(int j=0; j<arr.get(now).size(); j++) {
	                int next = arr.get(now).get(j);
	                
	                Q.add(next);
	            }    
	        }
	    }
	}
	
	public static int LCA(int a, int b) {
	    int ARoot = a;
	    int BRoot = b;
	    
	    while(nodes[ARoot].level > nodes[BRoot].level) {
	        ARoot = nodes[ARoot].parent;
	    }
	    
	    while(nodes[ARoot].level < nodes[BRoot].level) {
	        BRoot = nodes[BRoot].parent;
	    }
	    
	    // 여기 까지 오면 level 은 같은 상황이다 이제 부모가 같아야 한다
	    // 이렇게 적으면 ARoot 원래가 정답인 경우에 정답에 걸리지가 않는다 ! !!!! ! ! !  ! !!  !
	   // while(nodes[ARoot].parent != nodes[BRoot].parent) {
	   while(ARoot != BRoot) {
	        BRoot = nodes[BRoot].parent;
	        ARoot = nodes[ARoot].parent;
	    }
	    
	    return ARoot;
	}
	
	
}

이러한 문제가 결국에는 LinkedList를 이용한 구조이다 ! 