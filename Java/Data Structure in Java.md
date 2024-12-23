

## ArrayList




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

