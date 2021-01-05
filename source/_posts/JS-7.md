---
title: 7. 연산자
date: 2020-08-24 21:00:01
categories:
  - StudyLog
  - Javascript
tags: javascript
thumbnailImage: js.png
---

<!-- more -->

연산자는 규칙에 의해 결과를 나타내는 기호로 피연산자는 연산의 대상이 되어야 하므로 값으로 평가할 수 있어야 함.

<!-- excerpt -->
<!-- toc -->

<br>


- 연산자(operator) : 규칙에 의해 결과를 나타내는 기호
- 피연산자는 연산의 대상이 되어야 하므로 값으로 평가할 수 있어야 함

# 1) 산술 연산자

- 수 계산에 필요한 연산자
- 산술 연산이 불가능한 경우 NaN을 반환

  ## 1.1. 이항 산술 연산자

  - 2개의 피연산자를 산술 연산
  - 피연산자의 값을 변경하는 부수 효과(side effect)가 없음

  {% image center 7.1.jpg %}

  ## 1.2. 다항 산술 연산자

  - 1개의 피연산자를 산술 연산
  - 증가/감소(++/–) 연산자는 피연산자의 값을 변경하는 **부수 효과 존재**
  cf. 부수효과가 존재하는 연산자 :　증가,감소 연산자(++/--), 할당 연산자(=,+=,-=,*=,/=,%=), delete 연산자

  {% image center 7.2.jpg %}

<br>

  - 증가/감소(++/--) 연산자는 위치에 의미가 있다.

  ```jsx
  var x = 5,
    result;

  // 선할당 후증가(postfix increment operator)
  result = x++;
  console.log(result, x); // 5 6

  // 선증가 후할당(prefix increment operator)
  result = ++x;
  console.log(result, x); // 7 7

  // 선할당 후감소(postfix decrement operator)
  result = x--;
  console.log(result, x); // 7 6

  // 선감소 후할당 (prefix decrement operator)
  result = --x;
  console.log(result, x); // 5 5
  ```
  아래 두 예시에서도 연산자 위치에 따라 결과가 달라짐을 알 수 있다.

  ```js
  let i = 0;
  while (++i < 5) alert( i ); // 1 2 3 4 
  ```
  ```js
  let i = 0;
  while (i++ < 5) alert( i ); // 1 2 3 4 5
  ```
  <br>

  - **숫자 타입이 아닌 피연산자에 + 단항 연산자**를 사용하면
    → 피연산자를 **숫자 타입으로 변환**하여 반환

  ```jsx
  var x = "1";

  // 문자열을 숫자로 타입 변환한다.
  console.log(+x); // 1
  // 부수 효과는 없다.
  console.log(x); // "1"
  ```

  - **- 단항 연산자**는 피연산자의 **부호를 반전**한 값을 반환

  ```jsx
  // 부호를 반전한다.
  -(-10); // -> 10

  // 문자열을 숫자로 타입 변환한다.
  -"10"; // -> -10
  ```

  ## 1.3. 문자열 연결 연산자

  - 연산자는 피연산자 중 하나 이상이 문자열인 경우 **문자열 연결 연산자로 동작**

  ```jsx
  // 문자열 연결 연산자
  "1" + 2; // -> '12'

  // true는 1로 타입 변환된다.(암묵적 타입 변환)
  1 + true; // -> 2
  ```

<br>

# 2) 할당 연산자

- 좌항의 변수에 값을 할당하므로 변수 값이 변하는 부수 효과가 존재한다.
- 할당문→ 값으로 평가되는 표현식인 문!
  {% image center 7.3.jpg %}

<br>

# 3) 비교 연산자
## 3.1. 동등 / 일치 비교 연산자

{% image center 7.3.1.jpg %}

- 동등 비교(==) 연산자 : 암묵적 타입 변환을 통해 타입을 일치시킨 후, 같은 값인지 비교
- 일치 비교(===) 연산자 : 타입도 같고 값도 같은 경우에 한하여 true를 반환

```jsx
// 동등 비교
5 == "5"; // -> true

// 일치 비교
5 === "5"; // -> false
5 === 5; // -> true
```

- (🔴주의!) NaN은 자신과 일치하지 않는 유일한 값이다.

```jsx
NaN === NaN; // -> false
```

## 3.2. 대소 관계 비교 연산자

{% image center 7.3.2.jpg %}

<br>

# 4) 삼항 조건 연산자

- 📒 **삼항 조건 연산자** :　`조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false일 때 반환할 값`

```js
var x = 2;

// 삼항 조건 연산자 표현식은 표현식인 문이다. 따라서 값처럼 사용할 수 있다.
var result = x % 2 ? '홀수' : '짝수';
console.log(result); // 짝수
```

- if…else 문을 사용해도 삼항 조건 연산자 표현식과 유사하게 처리 가능하다.

```js
var x = 2, result;

if (x % 2) result = '홀수';
else       result = '짝수';

console.log(result); // 짝수
```
- 차이점 :
  삼항 조건 연산자 표현식은 값처럼 사용할 수 있지만
  if…else 문은 값처럼 사용할 수 없다.

```js
var x = 10;

// 삼항 조건 연산자 표현식은 표현식인 문이다. 따라서 값처럼 사용할 수 있다.
var result = x % 2 ? '홀수' : '짝수';
console.log(result); // 짝수
```
```js
var x = 10;

// if...else 문은 표현식이 아닌 문이다. 따라서 값처럼 사용할 수 없다.
var result = if (x % 2) { result = '홀수'; } else { result = '짝수'; };
// SyntaxError: Unexpected token if
```
<br>

# 5) 논리 연산자

- && :　모두 true면 true
- || :　모두 false면 false

{% image center 7.5.jpg %}
<br>

- 논리합(||) 또는 논리곱(&&) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다. 
논리합(||) 또는 논리곱(&&) 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다. ([9.4 단축평가](https://hanseul-lee.github.io/2020/08/25/JS-9/#4-%EB%8B%A8%EC%B6%95-%ED%8F%89%EA%B0%80) 참고)

```js
// 단축 평가
'Cat' && 'Dog'; // -> 'Dog'
```

- 드 모르간의 법칙

```js
!(x || y) === (!x && !y)
!(x && y) === (!x || !y)
```
<br>

# 6) 쉼표 연산자

- 왼쪽 피연산자부터 차례대로 피연산자를 평가하고 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평가 결과를 반환한다.

```jsx
var x, y, z;

(x = 1), (y = 2), (z = 3); // 3
```

<br>

# 7) 그룹 연산자

- 소괄호 ()로 피연산자를 감싼다.
- 연산자 우선순위가 가장 높다.

```jsx
// 그룹 연산자를 사용하여 우선순위를 조절
10 * (2 + 3); // -> 50
```

<br>

# 8) typeof 연산자

- 피연산자의 데이터 타입을 문자열로 반환
- 7가지 문자열 “string”, “number”, “boolean”, “undefined”, “symbol”, “object”, “function” 중 하나를 반환
- (🔴주의!) null 값을 연산해 보면 “null”이 아닌 “object”를 반환
  그러므로 값이 null 타입인지 확인할 때는 일치 연산자(===)를 사용할 것
- (🔴주의!) 선언하지 않은 식별자를 typeof 연산자로 연산해 보면 ReferenceError가 발생하지 않고 undefined를 반환

```js
typeof ''              // -> "string"
typeof 1               // -> "number"
typeof NaN             // -> "number"
typeof true            // -> "boolean"
typeof undefined       // -> "undefined"
typeof Symbol()        // -> "symbol"
typeof null            // -> "object"
typeof []              // -> "object"
typeof {}              // -> "object"
typeof new Date()      // -> "object"
typeof /test/gi        // -> "object"
typeof function () {}  // -> "function"

typeof undeclared; // -> undefined
```
<br>

# 9) 지수 연산자
- 좌항의 피연산자를 밑으로, 우항의 피연산자를 지수로 거듭 제곱한다.
- 지수 연산자는 **이항 연산자 중에서 우선순위가 가장 높다.**

```jsx
2 ** 2; // -> 4
2 ** 0; // -> 1
(-5) ** 2; // -> 25
```
# 10) 연산자의 부수 효과
일부 연산자는 다른 코드에 영향을 주는 부수 효과(side effect)가 있다. 부수 효과가 있는 연산자는 다음과 같다.
  - 증가/감소(++/–-) 연산자
  - 할당(=) 연산자
  - delete 연산자

```js
var x;

// 할당 연산자는 변수 값이 변하는 부수 효과가 있다.
// 이는 x 변수를 사용하는 다른 코드에 영향을 준다.
x = 1;
console.log(x); // 1

// 증가/감소 연산자(++/--)는 피연산자의 값을 변경하는 부수 효과가 있다.
// 피연산자 x의 값이 재할당되어 변경된다. 이는 x 변수를 사용하는 다른 코드에 영향을 준다.
x++;
console.log(x); // 2

var o = { a: 1 };

// delete 연산자는 객체의 프로퍼티를 삭제하는 부수 효과가 있다.
// 이는 o 객체를 사용하는 다른 코드에 영향을 준다.
delete o.a;
console.log(o); // {}
```
<br>

----
**Reference**
- poiemaweb.com