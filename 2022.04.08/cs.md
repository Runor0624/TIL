1. RESTful API에 대해 아는 만큼 설명하라.

- 현재 사용되는 API 설계 규칙가운데 → 가장 보편적으로 사용되는 규칙
- Restful API : Rest 특징을 준수 + 동시에 API를 제공한다는 의미
- FE에서 BE API를 호출시 url을 어떻게 만들것인지? 에 대한 이야기
- Restful API의 설계 규칙을 올바르게 준수한 시스템만 여기에 해당한다

1-1. Rest

- Rest(REpresentational State Transfer)
- 현대의 웹에서 사용되는 주요 개념임
- 웹의 장점을 극대화 시키기 위한 아키텍쳐로 로이 필딩 이라는 사람의 박사학위 논문에서 최초 소개됨
- 웹에 존재하는 모든 자원(이미지,영상 등)에 고유한 URI 부여 → 자원에 대한 주소를 지정하는 방법론 또는 규칙이다 → 가장 많이 사용된다

1-2. Rest 의 특징

- Uniform(유니폼 인터페이스)
  - URI로 지정한 리소스에 대한 조작을 통일되고 한정적 인터페이스로 수행하는 아키텍쳐 스타일을 말한다
- Stateless(무상태성)
  - REST는 무상태성 성격을 보유함 → 작업을 위한 상태정보를 별도로 저장하거나 관리하지 않음
  - API 서버는 들어오는 요청만 단순히 처리
  - 서비스의 자유도 향상 , 서버에서 불필요한 정보를 관리안함 → 구현의 단순화
- Cacheable(캐시 가능)
  - REST는 HTTP라는 기존의 웹 표준을 준수함 → 웹의 기존 인프라 그대로 활용가능
  - HTTP가 보유한 캐싱 기능이 적용가능함
- Self-descriptiveness(자체 표현 구조)
  - REST의 또 다른 특징중 하나는 REST API 메시지만 봐도 쉽게 이해가 가능하도록 자체 표현 구조로 구성됨
- Client - Server 구조
  - REST 서버는 API 제공, 클라이언트는 사용자 인증or컨텍스트 (로그인 정보등)을 관리하는 구조로 역할 구분 → 클라이언트와 서버가 상대에 대한 의존도 하락
- 계층형 구조
  - REST서버는 다중 계층으로 구성 가능 PROXY,게이트웨이등 네트워크 기반 중간매체 사용가능하도록 함

1-3. Restful API의 설계 규칙
REST API 설계시 중요한 규칙 2가지

- URI는 정보의 자원을 표현한다
- 자원에 대한 행위는 HTTP Method(GET,Post,PUT,Delete)로 표현함

- URI는 동사보다는 명사, 대문자보다는 소문자를 사용한다
- 마지막에 / 를 사용하지 않는다
  - 예제 : [https://www.wecode.co.kr/](https://www.wecode.co.kr/) (NG)
  - 예제 : [https://www.wecode.co.kr](https://www.wecode.co.kr) (OK)
- 언더바 대신 하이폰을 사용한다
  - 예제 [https://www.blog_Test.com](https://www.blog_Test.com) (NG)
  - 예제 [https://www.blog-Test.com](https://www.blog-Test.com) (OK)
- 파일 확장자는 URL에 포함하지 않는다
  - 예제 : [https://www.blog.com/123.png](https://www.blog.com/123.png) (NG)
  - 예제 : [https://www.blog.com/123](https://www.blog.com/123) (OK)
- 행위를 포함하지 않는다
  - 예제 : [https://www.blog.com/delete-post/1](https://www.blog.com/delete-post/1) (NG)
  - 예제 : [https://www.blog.com/post/1](https://www.blog.com/post/1) (OK)
