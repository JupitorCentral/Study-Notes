

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


### 배열을 index 에 따라 초기화 하기

-> int\[n] = {0, 1, 2, 3... n} 

``` java
int[] arr = IntStream.range(0, n).toArray();

int[] arr = new int[n+1];
Arrays.setAll(arr, i -> i);
```

### int[] 을 특정 값으로 초기화 하기 

``` java
int[] arr = {3, 5, 7}
```

### inline variable
``` java
return new int[]{4, 7}
```



