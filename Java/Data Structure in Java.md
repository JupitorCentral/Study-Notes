

## ArrayList


### Features

1.	Dynamic Resizing:<br>
	•	Unlike arrays in Java that have a fixed size, ArrayList automatically resizes itself when elements are added or removed.<br>
	•	Internally, it increases its size by 50% when the current capacity is exceeded.<br><br>
2.	Indexed Access:<br>
	•	Elements can be accessed and modified using an index, just like a standard array.<br>
	•	Indexing starts from 0.<br><br>
3.	Maintains Insertion Order:<br>
	•	Elements are stored and retrieved in the same order they were inserted.<br><br>
4.	Allows Duplicates:<br>
	•	It allows duplicate elements.<br>
    (Like, <br>
        list.add("Apple");<br>
        list.add("Banana");<br>
        list.add("Apple");)<br><br>
5.	Non-Synchronized:<br>
	•	ArrayList is not synchronized, meaning it is <b>not thread-safe</b> by default. If you need thread safety, you can use Collections.synchronizedList() or other concurrent alternatives like CopyOnWriteArrayList.<br><br>
6.	Supports Generics:<br>
	•	ArrayList can store a specific type of elements using generics, which ensures type safety at compile time.<br>


### Initialization

```java
ArrayList<String> list = new ArrayList<>();
```

ArrayList 의 배열도 된다. 가령

```java
ArrayList<Integer>[] arrayLists = new ArrayList[10];

```


## Deque
### Initiation of Deque

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


## PriorityQueue
### Initiation of PriorityQueue with custom comparator

``` java
PriorityQueue<Pair> pq = new PriorityQueue<>(o1, o2 -> {
    if (o1.value > o2.value) return 1;
    else if (o1.value < o2.value) return -1;
    else return 0;
});
```

return 값이 음수면 o1 이 더 앞에 오고, 양수면 o2 가 더 앞에 온다. 
(o1 returned when PriorityQueue.peek())

