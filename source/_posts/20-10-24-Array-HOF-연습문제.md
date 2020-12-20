---
title: "[과제] Array HOF 연습문제"
categories: [Fastcampus, 문제 풀이]
tags: []
thumbnailImage: HW.jpg
date: 2020-10-24 15:14:34
---

<!-- more -->
[과제] Array HOF 연습문제
<!-- excerpt -->

# 1. html 생성

- Q) 아래 배열을 사용하여 html을 생성하는 함수를 작성하라.

```js
const todos = [
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
];

/*
<li id="3">
  <label><input type="checkbox">HTML</label>
</li>
<li id="2">
  <label><input type="checkbox" checked>CSS</label>
</li>
<li id="1">
  <label><input type="checkbox">Javascript</label>
</li>
*/

```
<br>

- 풀이

```js
const todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
  ];

// 풀이1. forEach로 만들기
function render() {
  let html = '';

  todos.forEach(todo => {
     html += 
     `<li id = "${todo.id}">
          <label><input type="checkbox"${todo.completed ? ' checked' : ''}>${todo.content}</label>
      </li>`
  });   
return html;
};

// 풀이2. 풀이1을 디스터럭처링 할당을 이용해 바꾸기
function render() {
  let html = '';
  todos.forEach(todo => {
    const {id, content, completed} = todo;
      html += 
      `<li id="${id}">
        <label><input type="checkbox"${completed ?' checked': ''}>${content}</label>
      </li>`
    });
return html;
};

// 풀이3. map과 join으로 만들기
function render() {
    return todos
    .map(todo => {
        return `<li id = "${todo.id}">
        <label><input type="checkbox"${todo.completed ? ' checked' : ''}>${todo.content}</label>
    </li>`;
    })
    .join('');
}

console.log(render());
  /*
  <li id="3">
    <label><input type="checkbox">HTML</label>
  </li>
  <li id="2">
    <label><input type="checkbox" checked>CSS</label>
  </li>
  <li id="1">
    <label><input type="checkbox">Javascript</label>
  </li>
  */
```

<br>

# 2. 특정 프로퍼티 값 추출

- Q) 요소의 프로퍼티(id, content, completed)를 문자열 인수로 전달하면 todos의 각 요소 중, 해당 프로퍼티의 값만을 추출한 배열을 반환하는 함수를 작성하라.
단, for 문이나 Array#forEach는 사용하지 않도록 하자.

<br>

- 풀이

```js
const todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
  ];
  
function getValues(key) {
    return todos.map(todo => todo[key]);
};

// 화살표 함수(non-constructor)는 프로토타입을 만들지 않으므로 더 good
const getValues = key => todos.map(todo => todo[key]);

console.log(getValues('id')); // [3, 2, 1]
console.log(getValues('content')); // ['HTML', 'CSS', 'Javascript']
console.log(getValues('completed')); // [false, true, false]
```
<br>

# 3. 프로퍼티 정렬

- Q) 요소의 프로퍼티(id, content, completed)를 문자열 인수로 전달하면 todos의 요소를 정렬하는 함수를 작성하라.
단, todos는 변경되지 않도록 하자.

<br>

- 풀이

```js
const todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];
  
function sortBy(key) {
    return todos.sort((todo1, todo2) => 
            todo1[key] > todo2[key] ? 1 : (todo1[key] < todo2[key] ? -1 : 0)
    );
}

console.log(sortBy('id'));
/*
[
    { id: 1, content: 'Javascript', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 3, content: 'HTML', completed: false }
]
*/
console.log(sortBy('content'));
/*
[
    { id: 2, content: 'CSS', completed: true },
    { id: 3, content: 'HTML', completed: false },
    { id: 1, content: 'Javascript', completed: false }
  ]
  */
  console.log(sortBy('completed'));
  /*
  [
    { id: 3, content: 'HTML', completed: false },
    { id: 1, content: 'Javascript', completed: false },
    { id: 2, content: 'CSS', completed: true }
  ]
  */
```
<br>

# 4. 새로운 요소 추가
- Q) 새로운 요소(예를 들어 `{ id: 4, content: 'Test', completed: false }`)를 인수로 전달하면 todos의 선두에 새로운 요소를 추가하는 함수를 작성하라. 단, Array#push는 사용하지 않도록 하자.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

function addTodo(newTodo) {
    return [newTodo, ...todos];
}

// concat보다 위의 스프레드 문법을 쓰는 게 더 간편하다!
function addTodo(newTodo) {
  return todos = [newTodo].concat(...todos);
}

addTodo({ id: 4, content: 'Test', completed: false });

console.log(todos);
/*
[
  { id: 4, content: 'Test', completed: false },
  { id: 3, content: 'HTML', completed: false },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```
<br>

# 5. 특정 요소 삭제
- Q) todos에서 삭제할 요소의 id를 인수로 전달하면 해당 요소를 삭제하는 함수를 작성하라.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

function removeTodo(id) {
// filter는 accessor라 새로운 배열을 생성하기 때문에 
// 아래처럼 todos를 인수로 콘솔에 전달하려면 기존 todos에 덮어씌워 주어야 한다.
// 만약 아래처럼 return값에만 해주었다면 기존 todo를 출력했을 때 변화가 없다.
// return todos.filter(todo => todo.id !== id);

todos = todos.filter(todo => todo.id !== id);
}

removeTodo(2);

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: false },
  { id: 1, content: 'Javascript', completed: false }
]
*/
```
<br>

# 6. 특정 요소의 프로퍼티 값 반전
- Q) todos에서 대상 요소의 id를 인수로 전달하면 해당 요소의 completed 프로퍼티 값을 반전하는 함수를 작성하라.
hint) 기존 객체의 특정 프로퍼티를 변경/추가하여 새로운 객체를 생성하려면 Object.assign 또는 스프레드 문법을 사용한다.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

// 풀이1. 스프레드 문법 이용
function toggleCompletedById(id) {
         todos = todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
     );
}

// 풀이2. Object.assign 이용
function toggleCompletedById(id) {
    todos = todos.map(todo => 
        todo.id === id ? Object.assign({}, todo, {completed : !todo.completed}) : todo);
}

toggleCompletedById(2);

console.log(todos);
/*
[
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: false },
    { id: 1, content: 'Javascript', completed: false }
]
*/
```
<br>

# 7. 모든 요소의 completed 프로퍼티 값을 true로 설정
- Q) todos의 모든 요소의 completed 프로퍼티 값을 true로 설정하는 함수를 작성하라.
hint) 기존 객체의 특정 프로퍼티를 변경/추가하여 새로운 객체를 생성하려면 Object.assign 또는 스프레드 문법을 사용한다.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

// 풀이1. 스프레드 문법 사용
// 주의) 여기서 화살표 함수 몸체 () 생략하면 안됨!
// {}가 객체가 아닌 함수 몸체를 감싸는 중괄호가 되므로 
function toggleCompletedAll() {
    todos = todos.map(todo => ({ ...todo, completed: true}));
}

// 풀이2. 삼항연산자 사용
function toggleCompletedAll() {
  todos.map(todo => todo.completed === false ? todo.completed = true : todo.completed)
}

toggleCompletedAll();

console.log(todos);
/*
[
  { id: 3, content: 'HTML', completed: true },
  { id: 2, content: 'CSS', completed: true },
  { id: 1, content: 'Javascript', completed: true }
]
*/
```
<br>

# 8. completed 프로퍼티의 값이 true인 요소의 갯수 구하기
- Q) todos에서 완료(completed: true)한 할일의 갯수를 구하는 함수를 작성하라.
단, for 문, Array#forEach는 사용하지 않도록 하자.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

// filter는 자동적으로 true인 애들을 추출한다
// 그래서 굳이 todo.completed === true 이렇게 안써줘도 됨!
function countCompletedTodos() {
    return todos.filter(todo => todo.completed).length;
}

console.log(countCompletedTodos()); // 1
```
<br>

# 9. id 프로퍼티의 값 중에서 최대값 구하기

- Q) todos의 id 프로퍼티의 값 중에서 최대값을 구하는 함수를 작성하라.
단, for 문, Array#forEach는 사용하지 않도록 하자.

<br>

- 풀이

```js
let todos = [
    { id: 3, content: 'HTML', completed: false },
    { id: 2, content: 'CSS', completed: true },
    { id: 1, content: 'Javascript', completed: false }
];

// 방어코드를 짜지 않으면 
// todos가 빈 배열일 경우, 0이나 빈 배열을 반환하는게 아니라 -Infinity를 반환한다.
function getMaxId() {
    return todos.length ? Math.max( ... todos.map(todo => todo.id)) : 0;
}

console.log(getMaxId()); // 3
```

<br>
<br>