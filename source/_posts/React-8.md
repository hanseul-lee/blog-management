---
title: "[React] Hooks"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2021-01-01 13:34:22
updated:
---

<!-- more -->
리액트 v16.8에 새로 도입된 Hooks에 대해 알아봅시다.
<!-- excerpt -->
<!-- toc -->

*표시는 가장 빈번하게 사용되는 대표 Hooks 입니다.

<br>


# 1. useState*

> **동적 상태 관리**

`const [state, setState] = useState(initialState);`

- 상태 유지 값과 그 값을 갱신하는 함수를 반환

`state` = initial state
`setState` : state갱신 시 사용(Setter함수)

<br>

- 주의
함수를 호출 (X) / 함수를 전달 (O)
```html
<button onClick={onIncrease}>+1</button> // 전달
<button onClick={onIncrease()}>+1</button> // 호출하면 안됨
```

- 함수형 업데이트는 주로 나중에 컴포넌트를 최적화를 하게 될 때 사용
```js
const onIncrease = () => {
//	setNumber(number + 1);
    setNumber(prevNumber => prevNumber + 1);
}
```

<br>

# 2. useEffect*

> 리액트 컴포넌트가 **렌더링될 때마다** 특정 작업을 수행하도록 설정 **(2번째 파라미터가 바뀔때)**

<br>

- 사용 예시
    1. 마운트 될 때만 실행 (componentDidmount)
        - 2번째 파라미터(deps)로 **[] 빈배열**
    2. 특정 값이 업데이트될 때만 실행 (componentDidUpdate)
        - 2번째 파라미터(deps)로 **검사하고 싶은 값**
    3. 화면이 사라질때 실행 (componentWillUnmount)
    컴포넌트 언마운트 전이나 업데이트 직전
        - clean up함수 return

- cf. componentDidUpdate만 하고 싶을 때 패턴 (componentDidmount는 X)

```jsx
const mounted = useRef(false);
useEffect(() => {
	if (!mounted.current) {
		mounted.currnet = true;
	} else {
		// 실행하고 싶은 것
	}
}, [바뀌는 값])
```

<br>

# 3. useReducer

> **상태관리 (상태 업데이트 로직 분리)**

<br>

- 리액트에서 리덕스 구현 가능 (+ Contexted API)
- useState가 많아졌을 때, 이를 하나로 묶어 처리할 수 있게 줄여줌

`const [state, dispatch] = useReducer(reducer, { 기본값 });`
`state` : 현재 상태
`dispatch` : action을 발생시키는 함수
`reducer` : state와 action을 전달받아 새로운 상태를 반환하는 함수

<br>

- state는 직접 변경할 수 없고, 이벤트에서 action을 dispatch해서 변경
어떻게 바꿀 것인지는 reducer에 기록
- reducer함수에서 새로운 상태를 만들때는 반드시 불변성 지킬 것

```jsx
const [state, dispatch] = useReducer(reducer, { value: 0 });

<button onClick={() => dispatch({ type: 'INCREMENT' })}>+1</button>

function reducer(state, action) {
	return {...}; // 불변성을 지키면서 업데이트한 새로운 상태
}
```
<br>

- acrion의 이름은 대문자, 상수로 빼놓으면 좋음
`const SET_WINNER = 'SET_WINNER';`


<br>

# 4. useMemo

> **복잡한 함수 결과값을 기억해 연산 최적화(2번째 파라미터가 바뀌기 전까지)**

ex. 특정 값이 바뀌었을 때만 연산 실행 (list에 숫자 추가되었을때만 평균 계산)

- 처음엔 함수 안에 console.log 넣고 필요할 때만 실행되는지 꼭 확인! (Hook은 함수의 전체를 재실행하는 문제 존재)
- / cf. useCallback: 함수 자체를 기억
/ cf. useRef: 일반 값을 기억

<br>

# 5. useCallback

> **함수 재사용 - 함수 자체를 기억 (2번째 파라미터가 바뀌기 전까지)**
자식 컴포넌트에 props를 전달할 때 useCallback을 사용하지 않으면
렌더링 될 때마다 함수가 다시 생성되므로 자식은 props가 바뀌었다고 생각해 불필요한 리렌더링 발생
⇒ 따라서 useCallback 사용해 이를 방지

- props로 전달해야 할 함수를 만들 때는 useCallback을 사용하여 함수를 감싸는 것을 습관화하자.
- [] 빈 배열 넣으면 컴포넌트가 렌더링될 때만 함수 생성

<br>

# 6. useRef

**① 특정 DOM 선택**, **② 컴포넌트 안의 변수 관리**

- `ref` : ① React에서 DOM 선택 할 때 (input에 focus, 스크롤 위치 등)
          ② 컴포넌트 안에서 조회 및 수정 할 수 있는 변수를 관리할 때

    `useRef` : 함수형 컴포넌트에서 `ref` 사용 시 (Hook함수)

### 6.1 useRef - 특정 DOM 선택

`useRef()` 사용해 객체 만들고 원하는 DOM에 `ref` 값으로 설정하면 `.current` 는 우리가 원하는 DOM을 가리킴

```jsx
const nameInput = useRef();

const onReset = () => {
    setInputs({
      name: '',
      nickname: ''
    });
    nameInput.current.focus();
  };

return (
    <div>
      <input
        name="name"
        placeholder="이름"
        onChange={onChange}
        value={name}
        ref={nameInput}
			/>
```

- `useRef()` 를 사용 할 때 파라미터를 넣어주면, 이 값이 `.current` 의 기본값이 됨  ex) `const nextId = useRef(4);`

<br>

### 6.2 useRef - 컴포넌트 안 변수 관리

useState : 상태가 바뀌면 리렌더링
useRef : 상태가 바뀌어도 컴포넌트의 리렌더링이 되게 하고 싶지 않을 때 사용
               (ex. todos 배열의 id값)

- `setTimeout`, `setInterval` 을 통해서 만들어진 `id`
- 외부 라이브러리를 사용하여 생성된 인스턴스
- scroll 위치
- App 컴포넌트에서 `useRef` 를 사용해 변수 관리 → App에서 배열선언 후 UserList에게 props로 전달

<br>

---
**Reference**
- 김민준, 리액트를 다루는 기술
- 조현영 - 웹 게임을 만들며 배우는 React ([https://www.inflearn.com/course/web-game-React#](https://www.inflearn.com/course/web-game-React#))