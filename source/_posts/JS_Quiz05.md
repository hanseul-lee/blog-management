---
title: "[퀴즈] Javascript Quiz05 - 2020.10.23"
categories: [Fastcampus, 문제 풀이]
tags: [javascript]
thumbnailImage: js.png
date: 2020-10-23 19:57:02
---

<!-- more -->
Quiz05 오답 정리
범위 : 26.ES6 함수의 추가 기능 ~ 36.디스트럭처링 할당
<!-- excerpt -->
<!-- toc -->

# Quiz05 오답 정리
- 범위 : 26.ES6 함수의 추가 기능 ~ 36.디스트럭처링 할당
<br><br>


3. 아래 코드의 배열과 Map 메소드를 이용하여 배열 요소(각 문자열)의 길이를 출력하는 코드를 작성하시오.

```js
const dramas = ["응답하라 1997", "청춘기록", "호텔 델루나"];

// [9, 4, 6]
```
<br>

4. 아래 코드의 배열과 forEach 메소드를 이용하여 주석처리된 실행결과를 출력하는 코드를 작성하시오.

```js
const dramas = ["응답하라 1997", "응답하라 1994", "응답하라 1988"];

// 응답하라 1997는 응답하라 시리즈의 1번째 드라마입니다.
// 응답하라 1994는 응답하라 시리즈의 2번째 드라마입니다.
// 응답하라 1988는 응답하라 시리즈의 3번째 드라마입니다.
```
<br>

5. 아래 코드의 두 배열을 스프레드 문법을 이용하여 하나의 배열로 만드는 코드를 작성하시오.

```js
const cities = ["서울", "부산"];
const places = ["여수", "제주"];

// ['서울', '여수', '제주', '부산']
```
<br>

6. 아래 코드의 name, age, job 프로퍼티를 디스트럭처링 할당을 이용하여 fullName, age, job 변수에 각각 할당하는 코드를 작성하시오.

```js
let user = {
  name: "Lee Ungmo",
  age: 25,
  job: "teacher"
};
```
<br>

10. 아래 코드의 실행결과로 맞는 것은?

```js
function getAge(...args) {
  console.log(typeof args);
}
getAge(17);
```

- Number 
- Array 
- Object 
- NaN
<br><br>

---
# 풀이

3.

```js
const dramas = ["응답하라 1997", "청춘기록", "호텔 델루나"];

const result = dramas.map(drama => drama.length);
console.log(result); // [9, 4, 6]
```

4.

```js
const dramas = ["응답하라 1997", "응답하라 1994", "응답하라 1988"];

dramas.forEach((name, key) => {
    console.log(`${name}는 응답하라 시리즈의 ${key + 1}번째 드라마입니다.`)});

// 응답하라 1997는 응답하라 시리즈의 1번째 드라마입니다.
// 응답하라 1994는 응답하라 시리즈의 2번째 드라마입니다.
// 응답하라 1988는 응답하라 시리즈의 3번째 드라마입니다.
```

- forEach 메서드는 콜백 함수를 호출하면서 3개(요소값, 인덱스, this)의 인수를 전달한다.
- index는 0부터 시작하므로 `key`가 아니라 `key + 1`이다.
- forEach 메서드의 반환값은 언제나 undefined임을 주의하자. 따라서 다음과 같이 코드를 작성하면 undefined가 출력된다.
```js
const dramas = ["응답하라 1997", "응답하라 1994", "응답하라 1988"];

const result =  dramas.forEach((name, key) => {
    `${name}는 응답하라 시리즈의 ${key + 1}번째 드라마입니다.`
});
console.log(result); // undefirned
```
5.

```js
const cities = ["서울", "부산"];
const places = ["여수", "제주"];

cities.splice(1, 0, ...places);
console.log(cities); // ['서울', '여수', '제주', '부산']
```
- 배열의 중간에 다른 배열이의 요소들을 추가하거나 제거하려면 splice 메서드를 사용한다.

6.

```js
let user = {
    name: "Lee Ungmo",
    age: 25,
    job: "teacher"
  };

const {name: fullName, age, job} = user;

console.log(fullName, age, job); // Lee Ungmo 25 teacher
```

- 객체 디스트럭처링과 배열 디스트럭처링을 헷갈리지 말자. 
객체 디스트럭처링 할당의 우변은 객체이여야 한다. [name: fullName, age, job]이 아니다.
- 객체의 프로퍼티 키와 다른 변수 이름으로 프로퍼티 값을 할당받으려면 `name: fullName`과 같이 따로 프로퍼티 값을 할당해주어야 한다.


10.

```js
function getAge(...args) {
  console.log(args); // [17]
  console.log(typeof args); // Object
}
getAge(17);
```

17은 배열이 아니므로 ...은 스프레드 문법이 아니라 rest 파라미터이다. 따라서 17은 배열로 변환되고 배열은 type값이 Array가 아닌 Object이다. 스프레드 문법과 rest파라미터의 구분, 배열의 타입값이 무엇인지를 헷갈리지 말고 모두 정확히 알고 있어야 맞출 수 있는 문제였다.

<br><Br>