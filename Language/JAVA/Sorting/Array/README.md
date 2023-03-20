# Array 정렬

java.util.Arrays 의 **Arrays.sort()**

모든 primitive 타입과 Object[] 도 정렬이 가능하다.

```java
int[] arr = new int[] {4,7,56,234,98,63,1};
Arrays.sort(arr);//오름차순 정렬
```

이 메서드는 내부적으로 Dual-Pivot Quick Sort 알고리즘을 사용하며, 모든 데이터 셋에 대해 O(nlog(n))의 퍼포먼스를 보이고 일반적으로 기존의 One-Pivot Quick Sort 보다 빠르다.



- 부분 정렬

  ```java
  int[] arr = new int[] {4,7,56,234,98,63,1};
  Arrays.sort(arr,0,3);//부분 오름차순 정렬
  ```



- 병렬 정렬

  Arrays.sort()가 싱글쓰레드이고, Arrays.parallelSort()는 멀티쓰레드 기반으로 작동한다.



- 정렬 기준 커스터마이징

  Arrays.sort() 에 Comparator 객체를 파라미터로 넘겨 커스터마이징 한다.

  ```java
  Arrays.sort(arr,new Comparator<int>(){
  
      @Override
      public int compare(int o1, int o2) {
      	return o2-o1;
      }
  
  }); //내림차순 정렬
  ```

  ```java
  Arrays.sort(arr, (a,b)->b-a);//내림차순 정렬
  ```