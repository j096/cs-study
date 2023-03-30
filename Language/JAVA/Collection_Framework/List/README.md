# List<E>

List<E> 인터페이스를 구현하는 대표적인 컬렉션 클래스는 다음과 같다.

- ArrayList<E> : 배열 기반 자료구조, 배열을 이용하여 인스턴스 저장
- LinkedList<E> : 리스트 기반 자료구조, 리스트를 구성하여 인스턴스 저장

기능적 측면에서 완전히 동일하나, 인스턴스를 저장하는 방식에 차이가 있다.



List<E> 인터페이스를 구현하는 컬렉션 클래스들이 갖는 공통적인 특성

1. 인스턴스의 **저장 순서 유지**
2. 동일한 인스턴스의 **중복 저장 허용**



## ArrayList<E>

```java
import java.util.List;
import java.util.ArrayList;

class ArrayListCollection {
	public static void main(String[] args){
		List<String> list = new ArrayList<>();
		
		list.add("A");
		list.add("B");
		list.add("C");
		
		for(int i=0;i<list.size();i++){
			System.out.print(list.get(i));
		}
		
		list.remove(0);
	}
}
```



**ArrayList<E>가 아닌 List<E>형 참조변수를 선언한 이유는 코드에 유연성을 제공하기 위함이다.** ArrayList는 배열처럼 길이를 신경쓰지 않아도 된다. 단 ArrayList는 내부적으로 배열을 생성하여 인스턴스를 저장하므로, 배열의 길이를 늘리면 더 긴 배열로 교체를 한다. 따라서 성능에 신경을 써야 한다면 생성자에 길이를 파라미터로 넘겨주어 공간을 미리 확보해주는 것이 좋다.



- 단점
  - 저장 공간을 늘리는 과정에서 시간이 비교적 많이 소요된다.
  - 인스턴스의 삭제 과정에서 많은 연산이 필요할 수 있다. 따라서 느릴 수 있다. (배열 중간에 위치한 인스턴스를 삭제할 경우, 삭제된 위치를 비워 두지 않기 위해서 그 뒤에 저장되어 있느 인스턴스들을 한 칸씩 앞으로 이동하는 과정을 진행하게 된다.)
- 장점
  - 저장된 인스턴스의 참조가 빠르다. (어느 위치에 있는 인스턴스이건 인덱스 값을 통해 원하는 위치에 바로 접근 할 수 있다.)



## LinkedList<E>

```java
import java.util.List;
import java.util.LinkedList;

class LinkedListCollection {
	public static void main(String[] args){
		List<String> list = new LinkedList<>();
		
		list.add("A");
		list.add("B");
		list.add("C");
		
		for(int i=0;i<list.size();i++){
			System.out.print(list.get(i));
		}
		
		list.remove(0);
	}
}
```

LinkedList는 '연결 리스트(Linked List)' 라는 자료구조를 기반으로 디자인된 클래스이다. 따라서 인스턴스의 저장 및 삭제는 다음과 같은 방식으로 진행된다.

- 인스턴스 저장: 새로운 공간을 하나 추가로 연결하고, 그 공간에 인스턴스를 저장한다.
- 인스턴스 삭제: 해당 인스턴스를 저장하고 있는 공간을 삭제한다.

이렇듯 저장 공간을 열차 칸 추가하듯이 늘릴 수 있기 때문에 ArrayList와 달리 인스턴스의 저장 공간을 미리 마련해 둘 필요가 없다.



- 단점
  - 저장된 인스턴스의 참조 과정이 배열에 비해 복잡하다. 따라서 느릴 수 있다. (연결 리스트는 중간에 위치한 열차 칸에 바로 접근이 안된다. 제일 앞부터 또는 제일 뒤부터 한 칸씩 건너가야하는 구조이다.)
- 장점
  - 저장 공간을 늘리는 과정이 간단하다.
  - 저장된 인스턴스의 삭제 과정이 단순하다. (삭제하려는 공간을 빼고서 그 공간의 앞과 뒤를 연결하면 된다.)



## 저장된 인스턴스의 순차적 접근 방법

- for-each문 (enhanced for문)

  ```java
  for(String s : list)
  ```

  위와 같이 for-each문을 통한 순차적 접근의 대상이 되려면, 해당 컬렉션 클래스는 Iterable<T> 인터페이스를 구현해야 한다. Collection<E>가 Iterable<T>를 상속하고 있고, ArrayList, LinkedList가 Collection을 구현하고 있으므로 사용가능 하다.

- 반복자 (Iterator)

  ```java
  Iterator<String> itr = list.iterator();
  
  while(itr.hasNext()){
      str = itr.next();
      if(str.equals("Box"))
          itr.remove();
  }
  ```

  

## 컬렉션 변환

ArrayList는 인스턴스의 저장과 삭제가 편하고 반복자를 쓸 수 있으므로 배열보다 좋은 경우가 많지만, 배열처럼 '선언과 동시에 초기화'를 할 수 없다. 그래서 다음과 같이 컬렉션 인스턴스를 생성해야 한다.

```java
List<String> list = Arrays.asList("toy","robot","box");
```

그러나 이렇게 생성된 컬렉션 인스턴스는 새로운 인스턴스의 **추가나 삭제가 불가능**하다.

따라서 아래와 같이 생성자를 기반으로 인스턴스를 생성해야 한다.

```java
List<String> list = Arrays.asList("toy","robot","box");
list = new ArrayList<>(list);
```

- ArrayList<E>의 생성자

```java
class ArrayList<E>{
	public ArrayList(Collection<? extends E> c) {...}
	...
}
```

-> Collection<E>를 구현한 컬렉션 인스턴스를 인자로 받는다.

-> E는 인스턴스 생성 과정에서 결정되므로 무엇이든 될 수 있다.

-> 매개변수 c로 전달된 컬렉션 인스턴스에서는 참조만(꺼내기만) 가능하다.



대다수 컬렉션 클래스들은 다른 컬렉션 인스턴스를 인자로 전달받는 생성자를 가지고 있어서, 다른 컬렉션 인스턴스에 저장된 데이터를 복사해서 새로운 컬렉션 인스턴스를 생성할 수 있다.

ArrayList -> LinkedList 예시

```java
List<String> list = new ArrayList<>();

//list에 인스턴스 넣기
...

list = new LinkedList<>(list);
```



- 기본 자료형 데이터의 저장과 참조

  컬렉션 인스턴스도 기본 자료형의 값은 저장하지 못한다. 래퍼 클래스를 사용하여 저장 및 참조가 가능하며, 이 과정에서 오토 박싱과 오토 언박싱으로 인해 자연스러운 코드 구성이 가능하다.

  ```java
  LinkedList<Integer> list = new LinkedList<>();
  list.add(10);//오토 박싱
  list.add(20);
  list.add(30);
  
  int n = list.get(0);//오토 언박싱
  ```

  

## 양방향 반복자

List<E>를 구현하는 클래스의 인스턴스들만 얻을 수 있는 '양방향 반복자' (ListIterator<E>)가 있다.

```java
List<String> list = Arrays.asList("toy","robot","box");
list = new ArrayList<>(list);

ListIterator<String> litr = list.listIterator();

while(litr.hasNext()){//왼쪽에서 오른쪽으로 이동
	String str = litr.next();
	if(str.equals("toy"))
		litr.add("toy2");
}

while(litr.hasPrevious()){//오른쪽에서 왼쪽으로 이동
	String str = litr.previous();
	if(str.equals("robot"))
		litr.add("robot2");
}
```

-> next 호출 후에 add 하면, 앞서 반환된 인스턴스 뒤에 새 인스턴스 삽입

-> previous 호출 후에 add 하면, 앞서 반환된 인스턴스 앞에 새 인스턴스 삽입