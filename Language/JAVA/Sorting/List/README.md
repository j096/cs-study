# List 정렬

java.util.Collections.sort(List<T> list) 이용

```java
import java.util.*;
//...

List<Integer> list = new List<>();

//...list에 값 넣어줌

Collections.sort(list);//오름차순 정렬
Collections.sort(list, Comparator.reverseOrder());//내림차순 정렬
```

Collections.sort(List<T> list)는 merge sort 알고리즘을 이용하여 정렬한다.