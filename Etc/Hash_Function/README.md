# 해시함수 (Hash Function)
- 임의의 입력값을 <span style="background-color: rgba(242,179,188,0.5)">고정된 길이</span>의 해시값으로 변환하는 함수
- 해시값의 길이는 입력값의 길이와 상관없이 항상 동일하다.
	- 제 1역상 공격: 해시값으로 원본 복원
	- 제 2역상 공격: 서로 다른 입력값으로 같은 해시값 찾기
- 사용하는 곳:
	1. 비밀번호 검증
    2. 데이터 무결성 검증
- 종류: MD5, SHA-1, SHA-2(현재 가장 많이 사용)
- 속도: 안전한 해시 함수일수록 더 긴 길이를 사용한다. -> 계산하는데 드는 <span style="background-color: rgba(242,179,188,0.5)">비용이 커진다.</span>
- 실사용 예
	1. 비밀번호와 같은 민감한 데이터 보관 (Brute-force attack, DDoS에 취약(계산 비용이 크므로))
    <span style="color: rgba(0,0,256,1)">-> 보통 사용자가 비밀번호 평문을 서버로 보내면 서버에서 해시값으로 변환하여 사용한다. 사용자가 해시값으로 변환하여 서버로 전달하면 서버는 그대로 데이터베이스에 저장해버리기 때문에 해시값으로 변경하는 의미가 없어진다.(평문 유출은 https를 사용하는 것으로 방지한다.)</span>
   2. 바이너리 데이터의 무결성 검증
   -> 해시함수를 이용하여 바이너리 데이터를 고유 식별자로 만들어 같은 파일에 대한 저장 여부를 결정한다. (중복여부 결정) <span style="color: rgba(0,0,256,1)">ex) MurmurHash3</span>
- 문제점: <span style="background-color: rgba(242,179,188,0.5)">생성된 키가 많으면 많을수록 충돌 확률이 기하급수적으로 높아진다.</span>
- 해시함수 사용 시 고려사항:
	1. 입력값의 크기
	2. 보안 수준
	3. 해시값의 용도: 값 자체가 의미를 가지거나 식별자로 사용하는 경우
