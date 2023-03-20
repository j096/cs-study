# Map 정렬

Map은 key와 value 쌍으로 이루어진 자료구조이다.

HashMap은 순서와는 무관한 자료구조이기 때문에 정렬을 위해서는 LinkedHashMap을 이용해야 한다.

1. key를 기준으로 정렬

   Collections.sort(List list) 사용한다. 따라서 list로 변환 후 다시 LinkedHashMap으로 변환해주어야 한다.

   또한 List.sort(Comparator c)를 이용할 수도 있다.

   ```java
   HashMap<Intger, String> map = new HashMap();
   
   //...데이터 넣어줌
   
   List<Map.Entry<Integer, String>> entries = new ArrayList<>(map.entrySet());
   
   //1. List.sort
   entries.sort(Comparator.comparing(Map.Entry::getKey));
   //2. Collections.sort
   Collections.sort(entries, Comparator.comparing(Map.Entry::getKey));
   
   Map<Integer, String> sortedByKey = new LinkedHashMap<>();
   for(Map.Entry<Integer, String> entry : entries){
   	sortedByKey.put(entry.getKey(), entry.getValue());
   }
   ```

   

2. value를 기준으로 정렬

```java
HashMap<Intger, String> map = new HashMap();

//...데이터 넣어줌

List<Map.Entry<Integer, String>> entries = new ArrayList<>(map.entrySet());

//1. List.sort
entries.sort(Comparator.comparing(Map.Entry::getValue));
//2. Collections.sort
Collections.sort(entries, Comparator.comparing(Map.Entry::getValue));

Map<Integer, String> sortedByKey = new LinkedHashMap<>();
for(Map.Entry<Integer, String> entry : entries){
	sortedByKey.put(entry.getKey(), entry.getValue());
}	
```

