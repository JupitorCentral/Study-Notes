

### List, ArrayList, Linked 간의 관계


```markdown

java.lang.Object
    └── java.util.AbstractCollection<E>
            └── java.util.AbstractList<E>
                    └── java.util.ArrayList<E>
                    └── java.util.LinkedList<E>
    └── java.util.List<E> (인터페이스)
            ├── java.util.ArrayList<E>
            ├── java.util.LinkedList<E>
            ├── java.util.Vector<E>
            └── 기타 List 구현체

```

### List 인터페이스
```
	정의 : List는 Java Collections Framework의 일부로, 순서가 있는 요소의 컬렉션을 나타내는 인터페이스
	특징:
		순서 유지: 요소가 삽입된 순서를 유지합니다.
		중복 허용: 동일한 요소를 여러 번 포함할 수 있습니다.
		인덱스 접근: 특정 위치의 요소에 인덱스를 통해 접근할 수 있습니다.
```

### ArrayList 클래스

```
	정의: ArrayList는 List 인터페이스를 구현한 동적 배열 기반의 구현 클래스입니다.
	특징:
	    빠른 인덱스 접근: 임의의 인덱스에 대한 접근이 매우 빠릅니다 (O(1) 시간 복잡도).
	    동적 크기 조절: 요소가 추가될 때 내부 배열의 크기를 자동으로 조절합니다.
	    배열 기반: 내부적으로 배열을 사용하므로 메모리 효율이 좋습니다.
	단점:
	    중간에 요소를 삽입하거나 삭제할 때 상대적으로 느립니다 (O(n) 시간 복잡도).
```

### LinkedList 클래스
```
	정의: LinkedList는 List 인터페이스를 구현한 이중 연결 리스트 기반의 구현 클래스입니다.
	특징:
	    빠른 삽입 및 삭제: 리스트의 중간에 요소를 삽입하거나 삭제할 때 빠릅니다 (O(1) 시간 복잡도, 단 접근 시 O(n)).
	    노드 기반: 각 요소가 이전 및 다음 노드에 대한 참조를 가집니다.
	    메모리 사용량: 각 요소가 추가적인 참조(포인터)를 저장하므로 ArrayList보다 더 많은 메모리를 사용합니다.
	단점:
	    인덱스를 통한 임의 접근이 느립니다 (O(n) 시간 복잡도).
```


그러니까 List 는 인터페이스 이며, 이걸 변수로 쓰기 위해서 선언을
```java
List<List<Integer>> arr = new ArrayList<>();

```
이렇게 할 수 있으며, ArrayList 와 LinkedList 모두 List 의 구현 클래스 이므로
```java
List<List<Integer>> arr = new ArrayList<>();
arr = new LinkedList<>();
```
이렇게도 가능하다는 것이다.
