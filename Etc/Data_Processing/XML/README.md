## XML
- 웹에서 규격화된 데이터를 효율적으로 주고받기 위해 만든 마크업 언어
- 텍스트 기반으로 규격화된 데이터 표현
- 인코딩 직접 지정 가능하나 <span style="background-color: rgba(242,179,188,0.5)">인코딩 정보가 파일 안에 있어서 인코딩 정보를 읽으려면 파일의 인코딩 정보를 미리 알아야 한다.</span>
- XML 표준에는 <span style="background-color: rgba(242,179,188,0.5)">배열의 개념이 없다.</span> 동일한 이름의 요소가 여러 개 있을 때 이를 배열로 취급한다. 따라서 배열요소의 이름을 하나로 고정하여 사용하고 이를 <span style="background-color: rgba(242,179,188,0.5)">반복자</span>라고 한다.
- 사용 예시
```
<message>
	<number attribute="...">12344</number>
    <str_array>
    	<element> ... </element>
        <element> ... </element>
    <str_array>
</message>

<length unit="cm"> 100 </length>
or
<length>
	<value>100</value>
    <unit>cm</unit>
</length>
```
	- 요소: message, number, length 등
    - 반복자: element
    - 속성(attribute): attribute
- JSON이나 YAML은 파일을 항상 전체 내용을 파싱해야 하지만 xml은 <span style="background-color: rgba(242,179,188,0.5)">부분 파싱</span>이 가능하다.
- XML의 한계:
	- XML의 구조와 프로그래밍 언어에서 지원하는 객체의 형태가 1:1로 대응되지 않기 때문에 객체를 XML 파일로 만드는 방법은 JSON이나 YAML과 비교했을 때 조금 까다롭다.
	-> 배열 구분자를 element로 통일하고 속성을 사용하지 않으면 객체를 XML파일로 만들 수 있다.
