---
title: "[공부 기록] JavaScript - 프로토타입과 상속"
date: 2020-03-25 14:59:00
categories: JavaScript
---

Java나 C++같은 `class` 기반 언어에서는 `class`가 존재하지만 JavaScript에서는 `prototype` 기반 언어이기 때문에 (ES2015 부터)`class`라는 키워드를 제공하지만 내부적으로 `class`가 존재하는 것은 아니다.  
각각의 객체는 `[[Prototype]](__proto__)`이라는 `private` 속성을 가지는데 이것은 원형이 되는 `prototype` 객체를 가리키고 있다. 이 `prototype` 객체 또한 이 객체의 원형이 되는 `prototype` 객체를 가지고 있고 이것은 반복되다가 `null`을 프로토타입으로 가지는 객체에서 끝이 난다.  
이렇게 객체가 원형인 `prototype` 객체를 가리키는 것을 반복하는 것을 `prototype chain`이라고 한다.


## 1. Prototype
```js
function doSomething(){}
doSomething.prototype.foo = "bar";
```
// pic
```js
function doSomething(){}
doSomething.prototype.foo = "bar";

var doSomeInstancing = new doSomething();
doSomeInstancing.prop = "some value";
```
//pic2
```js
function doSomething(){}
doSomething.prototype.foo = "bar";

var doSomeInstancing = new doSomething();
doSomeInstancing.prop = "some value";

console.log("doSomeInstancing.prop:      " + doSomeInstancing.prop); // some value
console.log("doSomeInstancing.foo:       " + doSomeInstancing.foo); // bar
console.log("doSomething.prop:           " + doSomething.prop); // undefined
console.log("doSomething.foo:            " + doSomething.foo); // undefined
console.log("doSomething.prototype.prop: " + doSomething.prototype.prop); // undefined
console.log("doSomething.prototype.foo:  " + doSomething.prototype.foo); // bar
```
//pic3
prototype chain을 타고 가서 doSomeInstancing.foo는 bar이다.

## 2. Prototype을 이용한 상속

```js
let Human = function(name) {
  this.name = name;
}
Human.prototype.sleep = function() {};

let steve = new Human('steve');

let Student = function(name) {}
Student.prototype.learn = function() {};

let john = new Student('john');
john.learn();
john.sleep(); // 가능하게 하려면?
```
이 예제에서 `john.sleep()`이 가능해지려면 `Student`가 `Human`을 상속받아야 한다.  
정리하면 `john instanceof Student === true`를 만족해야 하고 동시에 `john instanceof Human === true`를 만족해야 한다.  
JavaScript에서 어떻게 상속을 할 수 있을까?

### 2-1. john.__proto__ = Human.prototype?
공식적으로 [[Prototype]]은 참조만 하기를 권장하고 있기 때문에 적절한 방법이 아니다.

### 2-2. Student.prototype = Human.prototype?
```js
Student.prototype = Human.prototype
Student.prototype.learn = funtion() {};
```
이렇게 하게 되면 말 그대로 `Student.prototype`과 `Human.prototype`이 같아지기 때문에 `Human`에서도 `learn()`을 호출할 수 있게 될 것이다.
이는 의도한 결과가 아니다.

### 2-3. Object.create()
```js
let Human = function(name) {
  this.name = name;
}
Human.prototype.sleep = function() {};

let steve = new Human('steve');

let Student = function(name) {
  Human.call(this, name);
}
Student.prototype = Object.create(Human.prototype);
Student.prototype.constructor = Student;
Student.prototype.learn = function() {};

let john = new Student('john');
john.learn();
john.sleep();
```
1. `Object.create()`를 사용하여 `Student`가 `Human`을 상속받도록 한다.
2. `Student.prototype.constructor`가 연결이 끊기기 때문에 `Student`로 다시 연결한다.
3. `this`연결이 끊기기 때문에 `Human.call(this, name);`으로 연결해준다.

## 3. class를 이용하여 상속하기 - ES6(ES2015)
```js
class Human {
  constructor(name) {
    this.name = name;
  }
  sleep() {}
}

let steve = new Human('steve');

class Student extends Human {
  constructor(name) {
    super(name);
  }
  learn() {}
}

let john = new Student('john');
john.learn();
john.sleep();
```
1. 함수 대신에 `class` 키워드를 쓴다.
2. `constructor`를 포함한다. 자식의 `constructor`가 부모의 것과 같을 경우 생략 가능하다.
3. 상속은 `extends` 키워드를 사용한다.
4. `super` 키워드로 부모의 객체를 가져올 수 있다.

## 4. 상속을 이용하여 Polymorphism(다형성) 표현하기.

### 4-1. prototype을 이용하여 Polymorphism(다형성) 표현하기.

### 4-2. class를 이용하여 Polymorphism(다형성) 표현하기.
```js
class Human {
  constructor(name) {
    this.name = name;
  }
  sleep() {
    console.log(this.name + ' is sleeping...');
  }
}

let steve = new Human('steve');

class Student extends Human {
  constructor(name) {
    super(name);
  }
  sleep() {
    console.log('Students never sleep.');
  }
  learn() {
    console.log(this.name + ' is learning something...');
  }
}

let john = new Student('john');
john.learn(); // john is learning something...
john.sleep(); // Students never sleep.
steve.sleep(); // steve is sleeping...
```

### Property 상속
JavaScript에서 객체는 자신이 가진 속성 뿐만아니라 자신이 가리키고 있는 `prototype chain`에 있는 모든 속성을 사용할 수 있다.

```js
// o라는 객체가 있고, 속성 'a' 와 'b'를 갖고 있다고 하자.
let f = function () {
    this.a = 1;
    this.b = 2;
}
let o = new f(); // {a: 1, b: 2}

// f 함수의 prototype 속성 값들을 추가 하자.
f.prototype.b = 3;
f.prototype.c = 4;

// f.prototype = {b: 3, c: 4}; 라고 하지 마라, 해당 코드는 prototype chain 을 망가뜨린다.
// o.[[Prototype]]은 속성 'b'와 'c'를 가지고 있다. 
// o.[[Prototype]].[[Prototype]] 은 Object.prototype 이다.
// 마지막으로 o.[[Prototype]].[[Prototype]].[[Prototype]]은 null이다. 
// null은 프로토타입의 종단을 말하며 정의에 의해서 추가 [[Prototype]]은 없다. 
// {a: 1, b: 2} ---> {b: 3, c: 4} ---> Object.prototype ---> null

console.log(o.a); // 1
// o는 'a'라는 속성을 가지는가? 그렇다. 속성의 값은 1이다.

console.log(o.b); // 2
// o는 'b'라는 속성을 가지는가? 그렇다. 속성의 값은 2이다.
// 프로토타입 역시 'b'라는 속성을 가지지만 이 값은 쓰이지 않는다. 이것을 "속성의 가려짐(property shadowing)" 이라고 부른다.

console.log(o.c); // 4
// o는 'c'라는 속성을 가지는가? 아니다. 프로토타입을 확인해보자.
// o.[[Prototype]]은 'c'라는 속성을 가지는가? 가지고 값은 4이다.

console.log(o.d); // undefined
// o는 'd'라는 속성을 가지는가? 아니다. 프로토타입을 확인해보자.
// o.[[Prototype]]은 'd'라는 속성을 가지는가? 아니다. 다시 프로토타입을 확인해보자.
// o.[[Prototype]].[[Prototype]]은 null이다. 찾는 것을 그만두자.
// 속성이 발견되지 않았기 때문에 undefined를 반환한다.
```

### Method 상속
JavaScript에서는 `method`개념이 없다. 하지만 객체에 `property`로 `함수`를 설정할 수 있고 `property`를 사용하듯 사용할 수 있다.  
하위 객체의 속성에 의해서 상위 객체의 속성이 가려졌을 경우에 `property`경우에서는 `property shadowing`이라고 하지만 `함수`의 경우에서는 `mothod overriding`이라는 용어를 사용한다.  

```js
var o = {
  a: 2,
  m: function(b){
    return this.a + 1;
  }
};

console.log(o.m()); // 3
// o.m을 호출하면 'this' 는 o를 가리킨다.

var p = Object.create(o);
// p 는 프로토타입을 o로 가지는 오브젝트이다.

p.a = 12; // p 에 'a'라는 새로운 속성을 만들었다.
console.log(p.m()); // 13
// p.m이 호출 될 때 'this' 는 'p'를 가리킨다.
// 따라서 o의 함수 m을 상속 받으며,
// 'this.a'는 p.a를 나타내며 p의 개인 속성 'a'가 된다.
```

## 객체를 생성하는 여러 가지 방법과 프로토타입 체인 결과
### 문법 생성자로 객체 생성
```js
var o = {a: 1};

// o 객체는 프로토타입으로 Object.prototype 을 가진다.
// 이로 인해 o.hasOwnProperty('a') 같은 코드를 사용할 수 있다.
// hasOwnProperty 라는 속성은 Object.prototype 의 속성이다.
// Object.prototype 의 프로토타입은 null 이다.
// o ---> Object.prototype ---> null

var a = ["yo", "whadup", "?"];

// Array.prototype을 상속받은 배열도 마찬가지다.
// (이번에는 indexOf, forEach 등의 메소드를 가진다)
// 프로토타입 체인은 다음과 같다.
// a ---> Array.prototype ---> Object.prototype ---> null

function f(){
  return 2;
}

// 함수는 Function.prototype 을 상속받는다.
// (이 프로토타입은 call, bind 같은 메소드를 가진다)
// f ---> Function.prototype ---> Object.prototype ---> null
```
### new 연산자(생성자 이용)
```js
function Graph() {
  this.vertexes = [];
  this.edges = [];
}

Graph.prototype = {
  addVertex: function(v){
    this.vertexes.push(v);
  }
};

var g = new Graph();
// g 'vertexes' 와 'edges'를 속성으로 가지는 객체이다.
// 생성시 g.[[Prototype]]은 Graph.prototype의 값과 같은 값을 가진다.
```
### Object.create 이용
```js
var a = {a: 1}; 
// a ---> Object.prototype ---> null

var b = Object.create(a);
// b ---> a ---> Object.prototype ---> null
console.log(b.a); // 1 (상속됨)

var c = Object.create(b);
// c ---> b ---> a ---> Object.prototype ---> null

var d = Object.create(null);
// d ---> null
console.log(d.hasOwnProperty); // undefined이다. 왜냐하면 d는 Object.prototype을 상속받지 않기 때문이다.
```
### class 키워드 이용
```js
'use strict';

class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

class Square extends Polygon {
  constructor(sideLength) {
    super(sideLength, sideLength);
  }
  get area() {
    return this.height * this.width;
  }
  set sideLength(newLength) {
    this.height = newLength;
    this.width = newLength;
  }
}

var square = new Square(2);
```
### 성능
존재하지도 않는 프로토타입의 접근을 위해서 프로토타입 체인을 전부 검사해야 해서 나쁜 성능을 보여주기도 한다.  
이를 해결하기 위해 `hasOwnProperty`를 사용하여 속성이 어디에 속해있는지 확인해서 프로토타입 체인 전부를 훑지 않도록 한다.

### Object.getPrototypeOf
인스턴스를 넣어서 `prototype`을 얻을 수 있는 함수이다.

출처  
Codestates Immersive Course
[mdn 상속과 프로토타입]  

[mdn 상속과 프로토타입]: https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain
