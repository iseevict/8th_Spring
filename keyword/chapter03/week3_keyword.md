# Keyword
#### RESTful API

REST 란?

- Representational State Transfer
- 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것
- 즉, HTTP URI 를 통해 자원 명시
- HTTP Method를 통해 해당 자원에 대한 동작 적용
- 구성요소 3가지
    - 자원(Resource) : HTTP URI
    - 자원에 대한 행위(Verb) : HTTP Method
    - 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load
- 특징 5가지
    - Server-Client 구조
    - Stateless (무상태)
    - Cacheable (캐시 처리 가능)
    - Layered System (계층화)
    - Uniform Interface (인터페이스 일관성)

REST API 란?

- REST 원리를 따르는 API
- 몇 가지 설계 규칙 존재
    - URI는 동사보단 명사, 대문자보단 소문자 사용
    - 마지막에 슬래시 포함하지 않음
    - 언더바 대신 하이픈 사용
    - 파일 확장자는 URI에 포함하지 않음
    - 행위 포함하지 않음

RESTful API 란?

- REST API 설계 규칙을 올바르게 지킨 시스템만이 RESTful 하다고 할 수 있음

#### 홈화면 API 전략

왜 이 키워드가 나왔는가?

- API 를 설계하다 보면 대부분 “홈 화면” 에 대한 API가 존재한다.
- 홈 화면은 대체로 여러 엔티티에서 데이터를 가져와서 보여준다.
- 그렇다면, 나는 API 하나에 모든 필요한 데이터들을 DTO 로 취합하여 클라이언트에게 응답을 해줘야 하는지, 홈화면에서 쓸 수 있도록 여러 API를 만들어 클라이언트가 알아서 가져다가 쓰게 해야 하는지 궁금해서 추가되었다.

하나의 API 로 응답하는 경우

- 하나의 호출로 모든 데이터를 받기에 네트워크 왕복 횟수를 줄일 수 있어 느린 연결 환경에서 유리
- 클라이언트가 편함
- 응답 데이터가 많아짐
- 홈화면에서 데이터 일부만 자주 업데이트되는 경우 전체 데이터를 캐싱하는 것이 비효율적

다중 API 로 응답하는 경우

- 클라이언트가 필요한 데이터만 선택적으로 불러오거나 컴포넌트 별로 비동기 로딩 구현 가능
- 각 엔드포인트에 대해 별도의 캐싱 전략 설정 가능 → 업데이트 빈도 낮은 데이터는 장기간 캐싱 가능
- 여러 번의 요청을 해야함 → HTTP 요청이 늘어남

유지보수 및 확장성 면

- 하나의 API
    - 단순한 클라이언트 로직
    - 복잡한 백엔드 로직
    - 강한 결합도
- 다중 API
    - 모듈화된 설계
    - 독립적 개발 : 팀별로 각 엔드포인트를 독립적으로 개발 가능
    - 클라이언트 복잡성 증가

위와 같은 상황에서 사용할 수 있는 패턴?방법?모델?

- BFF
- GraphQL
- API Gateway
- 등등..