# Set 정렬

Set은 기본적으로 순서를 보장하지 않기때문에 LinkedHashSet을 사용해야 한다.

Collections.sort()를 이용한다.

```java
Set<Integer> set = new LinkedHashSet<>();

//...데이터 입력

List<Integer> list = new ArrayList<>(set);
Collections.sort(list);
set = new LinkedHashSet<>(list);
```

