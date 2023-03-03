# DNS (Domain Name System)
- 호스트의 도메인 이름을 네트워크 주소로 바꾸거나 그 반대를 수행한다.
- 원리
1. 사용자가 주소창에 도메인 입력
2. Local DNS에게 ip 주소 질의
  -> 있으면 ip 주소 응답   
3. 없으면 Root DNS에 질의
4. Root DNS가 `.com` 관리하는 TLD(Top-Level Domain) 서버 정보 받음
5. TLD에 질의
6. TLD가 전체 도메인 관리 하는 DNS 정보 알려줌
7. 전체 도메인 관리 DNS 에 질의
8. Local DNS에게 ip 주소 응답
9. Local DNS는 ip 주소를 캐싱하고 클라이언트에게 전달
    
- 호스팅: 제공 사업자가 개인 홈페이지 서버 기능 대행하는 것. 기업의 대용량 메모리 공간을 이용하여 사용자의 웹 서버 기능 대행.
