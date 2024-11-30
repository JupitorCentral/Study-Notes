

## 헤더 테스트


### 헤더

```java
  public class Main {
      public static void main(String[] args) {
          try {
  
              Scanner sc = new Scanner(System.in);
              int n = sc.nextInt();
              int[] arr = new int[n];
  
              for (int i=0; i<n; i++){
                  arr[i] = sc.nextInt();
              }
  
          } catch (Exception e) {
              e.printStackTrace();
          }
```
