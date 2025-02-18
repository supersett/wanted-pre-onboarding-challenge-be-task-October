# :: 원티드 프리온보딩 챌린지 백엔드 코스 사전과제 안내
## 1-1) 사전과제 진행 가이드
- 아래 총 5 문제에 대한 해설을 해당 레포지토리를 fork 한 후 각 문제에 해당하는 파일에 작성해주세요.
- 문제 해설에 대한 정해진 양식은 없으며, 최대한 자세히 해설해주시면 더욱 좋습니다.
- 문제 유형은 해당 코스와 무관하게 면접을 준비한다면 알고 있으면 좋은 주제들을 몇 가지 선정하였습니다.

<br>

## 1-2) 사전 과제 
- (1) 동시에 같은 `DB Table row` 를 업데이트 하는 상황을 방어하기 위해 어떻게 개발하실 건지 설명해주세요.
- (2) `TCP` 와 `UDP` 의 차이를 작성해주세요.
- (3) 웹 브라우저에 `네이버` 를 검색하고 화면에 네이버 화면이 출력이 될 때 까지 내부적으로 어떤 동작들이 수행이 되는지 설명해주세요.
- (4) 본인이 주력으로 사용하는 언어에서 설계적 결함 한 가지를 작성해주세요.
- (5) 본인이 주력으로 사용하는 언어에서 자료구조와 관련 된 클래스가 내부적으로 어떻게 동작하는지 한 가지 사례를 정하여 작성해주세요. ex) `ArrayList`, `HashMap` 등등


## 답안 제출
# 1번
[상황] 여러 요청이 동시에 동일한 자원에 접근하고 수정하려 한다.
[해결방법]
→ 해당 데이터에 lock을 건다.
- lock으로 인해 데이터의 무결성을 보장하지만, 이후의 요청은 대기상태에 들어간다.
- data transaction의 write lock을 활용한다. 데이터를 수정할 때 write lock이 걸리고 transaction이 끝나야 lock이 풀린다.


# 2번
[TCP (Transmission Control Protocol)]
연결형 서비스를 지원하는 전송 계층 프로토콜
신뢰성 있는 데이터 전달과 흐름제어

[UDP(User Datagram Protocol)]
비연결형 서비스를 지원하는 전송계층 프로토콜
보내는 쪽에서 일방적으로 데이터를 전달
데이터를 데이터그램 단위로 처리하는 프로토콜

TCP는 연속성보다 신뢰성 있는 전송이 중요할 때 사용하는 프로토콜이고, UDP는 TCP보다 속도가 빠르고 네트워크 부하가 적다는 장점이 있지만, 신뢰성 있는 데이터 전송을 보장하지는 않는다.


# 3번
https://supersett-diary.tistory.com/233?category=1043720


# 4번
[설계적 결함]
테스트용 서버가 없음 → 실제 돌아가고 있는 서버로 테스트를 진행하고 있습니다.


# 5번
[HashMap]
Map 인터페이스를 구현한 collection class중 가장 많이 사용되는 클래스, hash 알고리즘을 사용하여 Key-Value형태로 저장한다.
Key 값은 중복이 되지 않도록 ‘Hashing(해싱)’이란 기술을 사용한다.

hashing : 문자열/object 등의 데이터를 좀더 짧고 인지하기 쉬운 숫자 등의 형태로 바꾸어 주는 것.

[해싱의 목적]
1.인덱싱 2.암호화,복호화 3.비교 용이
- 검색에 필요한 시간 O(n) → O(1)

[자바의 해싱 함수 hashCode()]
→ 내부적으로 각 값이 저장된 메모리 주소를 기반으로 해싱하여, 각 데이터가 고유의 인덱신된 값을 갖도록 하여 저장할 수 있게 된다.

[동작]
1. hashmap의 삽입 = PUT 메소드
2. Map.Entry Object
- 내부적으로 Key/Value 를 하나의 Map.entry 형태의 object로 만들어서 bucket에 저장한다.
- Entry는 Map의 중첩 인터페이스다.
3. 충돌 대처
- equals(), hashCode() 메소드를 통해 확인
- 동일한 해시값에 의해 동일한 위치에 Chaining 방식을 통해 저장한다.
4. 데이터 찾는법 (get method)
5. Load Factor
- 수용 가능한 크기가 어느 정도까지만 유지될 수 있는지에 대한 threshold 값



