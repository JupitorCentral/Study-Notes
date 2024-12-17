

### 이차원 배열

``` java
int[][] arr = new int[10][10];
```
이렇게 선언하면 10 * 10 크기의 배열이 생성되고, 모든 요소는 0으로 초기화된다.

### 가변 배열 (ragged array)

``` java
int[][] arr = new int[10][];
```
이렇게 선언하면 10 크기의 배열이 생성되고, 모든 요소는 null 로 초기화된다.
이를 사용하기 위해서는 각 행에 대한 배열을 따로 생성해야 한다.

``` java
arr[0] = new int[10];
arr[1] = new int[20];
arr[2] = new int[30];
```

## Non-Static Inner Class Behavior

A non-static inner class is tied to an instance of the outer class. This means:
### 1.	It cannot be instantiated without an instance of the outer class.
You need to create an instance of the outer class first.
###	2.	It has access to all members (including private) of the outer class.
This allows the inner class to use instance fields and methods of the outer class.
###	3.	It cannot have static members or methods because it depends on an instance of the outer class.


## Initiation of Deque

``` java
static public class Pair {
    int index;
    int value;
    public Pair(int index, int value) {
        this.index = index;
        this.value = value;
    }
}

... 

Deque<Pair> deque = new ArrayDeque<>();
```

At Deque, when you insert a variable, it is inserted at the end of the Deque.
It's FIFO, without any custom comparator.


## Initiation of PriorityQueue with custom comparator

``` java
PriorityQueue<Pair> pq = new PriorityQueue<>(o1, o2 -> {
    if (o1.value > o2.value) return 1;
    else if (o1.value < o2.value) return -1;
    else return 0;
});
```

return 값이 음수면 o1 이 더 앞에 오고, 양수면 o2 가 더 앞에 온다. 
(o1 returned when PriorityQueue.peek())







