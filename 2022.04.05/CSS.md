1. CSS 애니메이션과 JS 애니메이션의 차이를 설명하라
   1-1. CSS 애니메이션

- 메뉴 이동 , 버튼 전환 등의 애니메이션은 translate 등을 사용하여 처리 가능
- GPU 가속을 사용 → layout, paint 작업 생략가능
- 반응형으로 웹 구성시 → 미디어 쿼리를 통해 수월하게 구성가능
- 외부 라이브러리가 필수가 아니다.
- CSS: 선언형 → 특정 요소가 애니메이션을 보유해야한다 같은 직관적 표현
- UI요소가 작을 경우 사용하는게 권장됨

1-2.JS 애니메이션

- 사용자 눈에 가장 부드러운 60fps 달성 가능
- CSS로 처리하기에는 복잡하고 무거운 애니메이션 처리를 전담
- 요소의 스타일 변경시 마다 제어가능 → 세밀한 애니메이션 구성 가능
- 브라우저 호환성이 뛰어남 → JS애니메이션은 호환성에 구애받지 않음
- 애니메이션을 자세히 제어가 필요할 경우 사용하는걸 권장

1-3. 둘의 차이점

- 이전 버전 브라우저는 지원하지 않는 경우가 존재 , 특히 IE
- JS : 메인 쓰레드가 무거운 작업 진행중 → 애니메이션 우선순위 뒷순위로
- CSS: 독립적 쓰레드가 해당 애니메이션 처리 → CSS애니메이션 최적화 난이도 하락에 기여