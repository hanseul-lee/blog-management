---
title: 9. 타입 변환과 단축 평가
date: 2020-08-25 00:26:00
categories:
  - Fastcampus
  - Javascript
tags:
  - javascript
thumbnailImage: js.png
---

<!-- more -->

자신이 작성한 코드에서 암묵적 타입 변환이 발생하는지, 발생한다면 어떤 타입의 어떤 값으로 변환되는지, 그리고 타입 변환된 값으로 표현식이 어떻게 평가될 것인지 예측 가능해야 함.

<!-- excerpt -->
<!-- toc -->

# 1) 타입 변환

📒 **타입 변환 : 기존 원시값을 사용해 다른 타입의 새로운 원시값을 생성하는 것**
<br>

1. **암묵적 타입 변환, 타입 강제 변환(type coercion)** : 자바스크립트 엔진에 의한 강제적 타입 변환
2. **명시적 타입 변환, 타입 캐스팅(type casting)**: 개발자에 의한 의도적 타입변환

원시값은 변경 불가능한 값이므로 변경할 수 없다. 타입 변환은 기존 원시값을 직접 변경하는 것이 아닌 기존 원시값을 사용해 다른 타입의 새로운 원시값을 생성하는 것이다. 개발자는 자신이 작성한 코드에서 암묵적 타입 변환이 발생하는지, 발생한다면 어떤 타입의 어떤 값으로 변환되는지, 그리고 타입 변환된 값으로 표현식이 어떻게 평가될 것인지 예측 가능해야 한다.

# 2) 암묵적 타입 변환

## 2.1. 문자열 타입으로 변환
1. '+' 문자열 연결 연산자
  - '+' 연산자는 피연산자 중 하나 이상이 문자열이면 문자열 연결 연산자로 동작
2. 템플릿 리터럴
3. 공백 추가

```js
// 1. + 문자열 연결 연산자
1 + "2" // -> "12"

// 2. 템플릿 리터럴
`1 + 1 = ${1 + 1}`; // -> "1 + 1 = 2"

// 3. 공백 추가
0 +'' - // -> "0"
1 +''; // -> "-1"
true +''// -> "true"
[(10, 20)] + ''; // -> "10,20"
```


## 2.2. 숫자 타입으로 변환

- 산술 연산자

  피연산자를 숫자 타입으로 변환할 수 없는 경우 평가 결과는 NaN

```jsx
1 - "1"; // -> 0
1 * "10"; // -> 10
1 / "one"; // -> NaN
```

- 비교 연산자
  불리언 값을 만듦

```jsx
"1" > 0; // -> true
```

- 단항 연산자
  빈 문자열(‘’), 빈 배열([]), null, false는 0으로, true는 1로 변환
 객체와 빈 배열이 아닌 배열, undefined는 변환되지 않아 NaN이 된다.

```jsx
+"0"  // -> 0
+"1"  // -> 1
+"string"  // -> NaN

+true  // -> 1
+false  // -> 0

// null undefined의 값이 다르다는 것 구분해 알아두자!  
+null  // -> 0
+undefined  // -> NaN

+{}  // -> NaN
+[]  // -> 0
+[10, 20]  // -> NaN
+function () {}; // -> NaN
```

## 2.3. 불리언 타입으로 변환

- 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값(참으로 평가되는 값) 또는 Falsy 값(거짓으로 평가되는 값)으로 구분한다.
- Falsy 값(7개) :
  ***false , undefined, null, 0, -0, NaN, ’’ (빈 문자열)***
- Truthy 값:
  Falsy 값 외의 모든 값

```jsx
if ("") console.log("1");
if (true) console.log("2");
if (0) console.log("3");
if ("str") console.log("4");
if (null) console.log("5");

// 2 4
```

# 3) 명시적 타입 변환

## 3.1. 문자열 타입으로 변환

```js 
var x = 10;
console.log(String(x)); // 1. String 생성자 함수를 new 연산자 없이 호출
console.log(x.toString()); // 2. Object.prototype.toString 메서드를 사용
console.log(x + ''); // 3. 문자열 연결 연산자를 이용 
```

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메서드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법


```jsx
// 1. string 생성자 함수
String(1); // -> "1"
String(NaN); // -> "NaN"
String(true); // -> "true"

// 2. Object.prototype.toString 메서드
(1).toString(); // -> "1"
NaN.toString(); // -> "NaN"
true.toString(); // -> "true"

// 3. 문자열 연결 연산자 이용
1 + ""; // -> "1"
NaN + ""; // -> "NaN"
Infinity + ""; // -> "Infinity"
// 불리언 타입 => 문자열 타입
true + ""; // -> "true"
```

## 3.2. 숫자 타입으로 변환

1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 숫자 타입으로 변환 가능)
3. 단항 산술 연산자를 이용하는 방법
4. 산술 연산자를 이용하는 방법

```jsx
// 1. Number 생성자 함수
Number("0"); // -> 0
Number("-1"); // -> -1
Number(true); // -> 1

// 2. parseInt, parseFloat 함수를 사용
parseInt("0"); // -> 0
parseFloat('10.53'); // -> 10.53

// 3. + 단항 산술 연산자를 이용
+"0"; // -> 0
+"-1"; // -> -1
+true; // -> 1
+false; // -> 0

// 4. 산술 연산자를 이용
"0" * 1; // -> 0
true * 1; // -> 1
false * 1; // -> 0
```

## 3.3. 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
2. ! 부정 논리 연산자를 두 번 사용하는 방법

```jsx
// 1. Boolean 생성자 함수
Boolean("x"); // -> true
Boolean(""); // -> false
Boolean("false"); // -> true

Boolean(0); // -> false
Boolean(1); // -> true
Boolean(NaN); // -> false
Boolean(Infinity); // -> true

Boolean(null); // -> false
Boolean(undefined); // -> false

// 2. ! 부정 논리 연산자를 두 번 사용
!!"x"; // -> true
!!""; // -> false
!!"false"; // -> true

!!0; // -> false
!!1; // -> true
!!NaN; // -> false
!!Infinity; // -> true

!!null; // -> false
!!undefined; // -> false
```

# 4) 단축 평가

## 4.1. 논리 연산자를 사용한 단축 평가

- 📒 **단축 평가** : 표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평가 과정을 생략하는 것

논리합(||) 연산자와 논리곱(&&) 연산자 표현식의 평가 결과는 **불리언 값이 아닐 수도 있다.** 
이때 논리합(||), 논리곱(&&) 연산자 표현식은 **언제나 2개의 피연산자 중 어느 한쪽으로 평가**된다. 
<br>

- 단축 평가 규칙

```jsx
true || anything; // true
false || anything; // anything
true && anything; // anything
false && anything; // false
```
<br>

- 예제

```jsx
"Cat" && "Dog"; // -> "Dog"
```

논리곱(&&) 연산자는 두 개의 피연산자가 모두 true로 평가될 때 true를 반환
여기서 'Cat'은 true
그러므로 뒤의 'Dog'에 의해 결과값 결정됨
논리곱 연산자는 **논리 연산의 결과를 결정하는 두 번째 피연산자**, 즉 문자열 ‘Dog’를 그대로 반환!
<br>

마찬가지로 논리합(||) 연산자는 두 개의 피연산자 중 하나만 true로 평가되어도 true를 반환하므로 결과를 결정하는 첫 번째 피연산자, 문자열 ‘Cat’을 그대로 반환한다.
```jsx
"Cat" || "Dog"; // -> "Cat"
```

<br>

- 단축 평가를 사용하면 if 문을 대체 가능하다.

1. 주어진 조건이 true

```jsx
var done = true;
var message = "";

// 주어진 조건이 true일 때
if (done) message = "완료";

// if 문은 단축 평가로 대체 가능하다.
// done이 true라면 message에 '완료'를 할당
message = done && "완료";
console.log(message); // 완료
```

2.  주어진 조건이 false

```jsx
var done = false;
var message = "";

// 주어진 조건이 false일 때
if (!done) message = "미완료";

// if 문은 단축 평가로 대체 가능하다.
// done이 false라면 message에 '미완료'를 할당
message = done || "미완료";
console.log(message); // 미완료
```

3.  if...else 문

```jsx
var done = true;
var message = "";

// if...else 문
if (done) message = "완료";
else message = "미완료";
console.log(message); // 완료

// if...else 문은 삼항 조건 연산자로 대체 가능하다.
message = done ? "완료" : "미완료";
console.log(message); // 완료
```
<br>

- 객체를 가리키기를 기대하는 변수가 null 또는 undefined이 아닌지 확인하고 프로퍼티를 참조할 때

```js
var elem = null;
var value = elem.value; // TypeError: Cannot read property 'value' of null
```
```js
var elem = null;
// elem이 null이나 undefined와 같은 Falsy 값이면 elem으로 평가되고
// elem이 Truthy 값이면 elem.value로 평가된다.
var value = elem && elem.value; // -> null
```
<br>

- 함수 매개변수에 기본값을 설정할 때
함수를 호출할 때 인수를 전달하지 않으면 매개변수는 undefined를 갖는다. 이때 단축 평가를 사용하여 매개변수의 기본값을 설정하면 undefined로 인해 발생할 수 있는 에러를 방지할 수 있다.

```js
// 단축 평가를 사용한 매개변수의 기본값 설정
function getStringLength(str) {
  str = str || '';
  return str.length;
}

getStringLength();     // -> 0
getStringLength('hi'); // -> 2

// ES6의 매개변수의 기본값 설정
function getStringLength(str = '') {
  return str.length;
}

getStringLength();     // -> 0
getStringLength('hi'); // -> 2
```
<br>

## 4.2. 옵셔널 체이닝 연산자

📒 **옵셔널 체이닝(optional chaining) 연산자 :　?.**

좌항이 null 또는 undefined → undefined
그렇지 않으면 우항의 프로퍼티 참조를 이어감

- 객체를 가리키기를 기대하는 변수가 null 또는 undefined이 아닌지 확인하고 프로퍼티를 참조할 때 유용하다.

## 4.3. null 병합 연산자

📒 **null 병합(nullish coalescing) 연산자 :　??**

좌항이 null 또는 undefined → 우항의 피연산자를 반환
그렇지 않으면 좌항의 피연산자를 반환

- 변수에 기본값을 설정할 때 유용하다.


<br>

----
**Reference**
- poiemaweb.com