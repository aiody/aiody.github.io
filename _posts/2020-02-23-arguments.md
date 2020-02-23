---
title: "[공부 기록] JavaScript - arguments"
date: 2020-02-23 13:54:00
categories: JavaScript arguments function
---

## 정의
`arguments`는 함수의 매개변수들의 배열형의 객체이다. 함수에 처음부터 갖고 있는 숨겨진 속성이기 때문에 매개변수 자리에 선언하지 않아도 사용할 수 있다.

```javascript
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1

  console.log(arguments[1]);
  // expected output: 2

  console.log(arguments[2]);
  // expected output: 3
}

func1(1, 2, 3);
```

## 특징
`arguments`는 유사배열로 배열처럼 생겼지만 `length`를 빼고는 어떤 배열 메소드를 사용할 수 없다.
`Array`로 변환하기 위해서는 아래처럼 쓸 수 있다.

```javascript
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);
```
또는 아래와 같이 ES2015의 `Array.from()`메소드 또는 `spread operator`를 사용할 수도 있다.

```javascript
var args = Array.from(arguments);
var args = [...arguments];
```



## 왜 정리했나?
`arguments`를 공부하며 헷갈렸던 부분은 매개변수를 명시했을 때도 쓸 수 있고 명시하지 않아도 쓸 수 있는 점이었다.
그래서 아래처럼 테스트를 해보고 나서는 `a`와 `arguments[0]`이 같다는 것을 이해했다.

```javascript
// 매개변수를 명시했을 때
function FuncTest1 (a) {
  console.log(arguments[0]);
  console.log(a === arguments[0]);
}

FuncTest1(1); // expected output: 1, true

// 매개변수를 명시하지 않았을 때
function FuncTest2() {
  console.log(arguments[0]);
}

FuncTest2(1); // expected output: 1
```


출처 : <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments>
