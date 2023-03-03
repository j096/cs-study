# JSON (JavaScript Object Notation)
- JavaScript에서 객체를 만들 때 사용하는 표현식
- 여러 형태의 데이터를 key-value로 구조화된 객체에 담아 처리하는 규격이다.
- 텍스트 기반이며 서버와 클라이언트 간 메시지 표준 규격 중 하나이다.
- <span style="background-color: rgba(242,179,188,0.5)">UTF-8만 허용</span>하며 주석이 불가능하다. (주석이 필요하다면 XML, YAML 처럼 주석을 지원하는 메시지 규격을 사용해야 한다.)
- 사용 예시
```
{
	"key1": number("text"),
    "object": {
    			"key2":"value"
    		  },
     "array":[1,2,3,4,5],
     "array1":["1","2","3"]
}
```
	-> "["로 시작할 시 배열에는 숫자, 문자, 객체 중 한가지만 가능
    -> 큰 따옴표는 \" 로 표헌
- 읽어들인 JSON 데이터를 클래스, 맵, 리스트 등의 객체로 변환하는 것을 <span style="background-color: rgba(242,179,188,0.5)">역직렬화</span>라고 한다. 반대는 <span style="background-color: rgba(242,179,188,0.5)">직렬화</span>
- 객체나 배열요소는 전달하는 소프트웨어 로직이나 라이브러리에 의해 <span style="background-color: rgba(242,179,188,0.5)">순서가 바뀔 수 있다.</span>
- JSON의 한계:
	1. 텍스트 기반이기 때문에 데이터를 표현하는데 드는 <span style="background-color: rgba(242,179,188,0.5)">비용이 크다.</span>
    2. 모든 텍스트 기반 데이터의 단점이기도 한 유지보수의 어려움이 있다.
    -> 규격 업데이트시 클라이언트도 모두 반영되어야 한다.<span style="color: rgba(0,0,256,1)">(RESTful API를 사용할 때 버전을 주소에 넣어 해결하기도 한다.)</span>
