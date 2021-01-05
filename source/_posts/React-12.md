---
title: "[React] Router : history, match, location"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2020-12-24 10:05:17
---

<!-- more -->
history, match, location은 리액트 라우트로 사용된 컴포넌트에 전달되는 props 중 하나로, 이 객체들를 통해 컴포넌트 내에 구현하는 메서드에서 라우터 API를 호출할 수 있다.  
<!-- excerpt -->

# Router props

history, match, location은 리액트 라우트로 사용된 컴포넌트에 전달되는 props 중 하나로, 이 객체들를 통해 컴포넌트 내에 구현하는 메서드에서 라우터 API를 호출할 수 있다. 

`console.log(props)`를 해주면 다음과 같은 결과를 볼 수 있다.

<br>

{% image center 2020-12-24-14-29-52.png 700px console.log(props) %}


반환된 객체(props)에서 history, location, match가 담겨있는 것을 확인할 수 있다.


<Br>

## history
history 객체는 브라우저의 history와 유사하다. 
스택(stack)에 현재까지 이동한 url 경로들이 담겨있는 형태로 주소를 임의로 변경하거나 되돌아갈 수 있도록 해준다. 
history객체는 mutable하므로 history.location보다는 location을 직접 사용해 주기를 권장한다.

<Br>

{% image center 2020-12-24-14-38-17.png 700px %}

<Br>

- **action** : [string] 최근에 수행된 action (PUSH, REPLACE or POP)
- **block(prompt)** : [function] history 스택의 PUSH/POP 동작을 제어
- **go(n)** : [function] : history 스택의 포인터를 n번째로 이동
- **goBack()** : [function] 이전 페이지로 이동
- **goForward()** : [function] 앞 페이지로 이동
- **length** : [number] 전체 history 스택의 길이
- **location** : [JSON object] 최근 경로 정보
- **push(path, [state])** : [function] 새로운 경로를 history 스택으로 푸시하여 페이지를 이동
- **replace(path, [state])** : [function] 최근 경로를 history 스택에서 교체하여 페이지를 이동


<Br>

```js
// 뒤로 이동
handleGoBack = () => {
  this.props.history.goBack();
};

// 홈으로 이동
handleGoHome = () => {
  this.props.history.push('/');
};

componentDidMount() {
  // 페이지에 변화가 생기려고 할 때마다 정말 나갈 것인지 질문함
  this.unblock = this.props.history.block('정말 돌아가시겠습니까?');
}
```

<Br>

## location
**location 객체에는 현재 페이지의 정보를 가지고 있다.** 
대표적으로 location.search로 현재 url의 쿼리 스트링을 가져올 수 있다.


<Br>

{% image center 2020-12-24-14-41-01.png 700px %}

<Br>

- 예제1

```jsx
<Route
  render={({ location }) => (
    <div>
      <h2>존재하지 않는 페이지 입니다.</h2>
      <p>{location.pathname}</p>
    </div>
  )}
/>
```

- 예제2

```js
const About = ({ location }) => {
  const query = qs.parse(location.search, {
    ignoreQueryPrefix: true, // 문자열 맨 앞의 ? 생략
  });
  const showDetail = query.detail === 'true'; // 쿼리의 파싱 결과값은 항상 문자열이라는 것에 주의

  return (
    <div>
      <h1>소개</h1>
      <p>안녕하세요 라라랜드 맛있는 레몬워터입니다.</p>
      {showDetail && <div>제가 제일 좋아하는 음료수랍니다.</div>}
    </div>
  );
};
```

<br>

## match
**match 객체에는 'Route path'와 URL이 매칭된 것에 대한 정보가 담겨져있다.** 
대표적으로 match.params로 path에 설정한 파라미터값을 가져올 수 있다.

<Br>

{% image center 2020-12-24-14-42-05.png 700px %}

<Br>

- **isExact** : [boolean] true일 경우 전체 경로가 완전히 매칭될 경우에만 요청을 수행
- **params** : [JSON object] url path로 전달된 파라미터 객체 
- **path** : [string] 라우터에 정의된 path
- **url** : [string] 실제 클라이언트로부터 요청된 url path

<Br>

```js
const Profile = ({ match }) => {
  const { username } = match.params;
  const user = data[username];

  if (!user) {
    return <div>존재하지 않는 사용자입니다.</div>;
  }

  return (
    <div>
      <h3>{user.name}의 프로필</h3>
      <p>{user.description}</p>
    </div>
  );
};
```

<br>

---
**Reference**
- 김민준, 리액트를 다루는 기술
- [https://reactrouter.com/web/api/history](https://reactrouter.com/web/api/history)
- [https://gongbu-ing.tistory.com/45](https://gongbu-ing.tistory.com/45)
- [https://medium.com/@han7096/react-router-v4-%EC%A0%95%EB%A6%AC-e9931b63dcae](https://medium.com/@han7096/react-router-v4-%EC%A0%95%EB%A6%AC-e9931b63dcae)