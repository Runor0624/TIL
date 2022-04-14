1. Recoil은 무슨 기능을 하는가?

- Redux와 유사한 상태 관리 라이브러리임.
  - Vue 등 에서도 사용가능한 라이브러리인 Redux와 달리 React에서만 사용함.
  - React에 필요한거만 리액트에서 사용하기 쉽도록 제작된 라이브러리
  - 리액트를 제작한 페이스북( 현 메타)에서 출시함.
- 리덕스와 유사한 업무를 담당하나 리덕스 보다 순한맛의 러닝커브를 보유한다

### RecoilRoot

- root 컴포넌트에 RecoilRoot를 넣어서 사용한다
  - 왜? : recoil 상태를 사용할려는 컴포넌트는 부모 어딘가에서 등장하는 RecoilRoot가 필요함
    - 뭔소리여? : recoil쓸려면 최상단 root 컴포넌트에 RecoilRoot감싸서 사용해야함.

<!-- import React from 'react';
import {
  RecoilRoot,
  atom,
  selector,
  useRecoilState,
  useRecoilValue,
} from 'recoil';

function App() {
  return (
    <RecoilRoot>
      <CharacterCounter />
    </RecoilRoot>
  );
} -->

### Atom

- state(상태)의 일부를 나타낸다, 리덕스의 Store와 유사하며 상태의 단위이다.
- Atom에 변화가 발생한다? → Atom을 구독하는 모든 컴포넌트를 재 렌더링시킨다.
- key : 유니크한 id값, 여러 컴포넌트에서 Atom 구독시 → 컴포넌트들도 동일한 상태를 공유함.

<!-- const textState = atom({
  key: 'textState', // unique ID (다른 atoms/selectors 와 구분하기 위함)
  default: '', // default value (aka initial value), [] 등 저장되는 값 지정가능
}); -->

### useRecoilState

<!-- function CharacterCounter() {
  return (
    <div>
      <TextInput />
      <CharacterCount />
    </div>
  );
}

function TextInput() {
  const [text, setText] = useRecoilState(textState);

  const onChange = (event) => {
    setText(event.target.value);
  };

  return (
    <div>
      <input type="text" value={text} onChange={onChange} />
      <br />
      Echo: {text}
    </div>
  );
} -->

<!-- const [text, setText] = useRecoilState(textState) -->

- text는 textState의 value를 보유 - state가 여기로 들어감
- setText는 text의 값을 변경한다 - setState 가 여기로 들어감
  - React의 useState 사용하는 방법과 유사하다.
- Atom의 state에 모든 컴포넌트를 전역으로 받거나, setText등 setState로 state변경 가능
  - 이걸 통해 변경하면 → 이걸 사용하는 컴포넌트는 모두 재 렌더링을 실시한다.

### useRecoilValue + useSetRecoilValue

<!-- function TextInput() {
 // const [text, setText] = useRecoilState(textState);
const text = useRecoilValue(textState);
const setText = useSetRecoilValue(textState);

  const onChange = (event) => {
    setText(event.target.value);
  }; -->

- useRecoilState와 무슨 차이인가?
  - useRecoilState 반으로 갈라버리고 쓰는것임
  - state와 setState를 분리하였으나 이 둘은 useRecoilState가 하던 역할을 그대로 담당한다.
    - 얘네 둘이 뭉치면 useRecoilState 기능을 그대로 수행함.

### Selector

- 공식문서에는 Selector가 파생된 상태(derived State)의 일부를 나타냄, 파생된 상태는 상태의 변화이며
- 파생된 상태는 어떤 방법으로든 주어진 상태를 수정하는 **순수 함수에 전달된 상태의 결과물**임.
  - 순수함수: 동일한 입력값 → 동일한 출력값을 보유한 함수
  - 읽기전용인 RecoilValueReadonly 객체임 → 리턴값만 보유가능, set으로 값 변경 불가능

<!-- const charCountState = selector({
  key: 'charCountState', // unique ID (with respect to other atoms/selectors)
  get: ({get}) => {
    const text = get(textState);

    return text.length;
  },
}); -->

- get 프로퍼티를 통해 → state를 가공 →derived State를 반환한다.
- atom의 textState를 가공 → length값을 리턴받는다.
