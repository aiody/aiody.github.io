---
title: "[공부 기록] JavaScript - 프로토타입과 상속"
date: 2020-03-25 14:59:00
categories: JavaScript
---

Java나 C++같은 `class` 기반 언어에서는 `class`가 존재하지만 JavaScript에서는 `prototype` 기반 언어이기 때문에 (ES6/ES2015부터)`class`라는 키워드를 제공하지만 내부적으로 `class`가 존재하는 것은 아니다.  
각각의 객체는 `[[Prototype]](__proto__)`이라는 `private` 속성을 가지는데 이것은 원형이 되는 `prototype` 객체를 가리키고 있다. 이 `prototype` 객체 또한 이 객체의 원형이 되는 `prototype` 객체를 가지고 있고 이것은 반복되다가 `null`을 프로토타입으로 가지는 객체에서 끝이 난다.  
이렇게 객체가 원형인 `prototype` 객체를 가리키는 것을 반복하는 것을 `prototype chain`이라고 한다.


## 1. Prototype
```js
function doSomething(){}
doSomething.prototype.foo = "bar";
```
위의 코드를 실행시키면 내부적으로는 아래의 그림처럼 `doSomething`의 `prototype`과 `function`이 생기고 둘 사이에는 `constructor`와 `prototype` 속성을 통해 연결된다.
![prototype](https://user-images.githubusercontent.com/11348329/77530161-43edc700-6ed4-11ea-83ab-8d44a314f4b7.jpg)

```js
function doSomething(){}
doSomething.prototype.foo = "bar";

var doSomeInstancing = new doSomething();
doSomeInstancing.prop = "some value";
```
`doSomething`으로 `doSomeInstancing`이라는 인스턴스를 생성하게 되면 아래의 그림처럼 `doSomeInstancing`의 `__proto__`가 `doSomething`의 `prototype`을 가리키게 된다.
![prototype_and_instance](https://user-images.githubusercontent.com/11348329/77530165-451ef400-6ed4-11ea-9334-0199853403cf.jpg)

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
위의 코드처럼 로그를 찍어보게 되면 아래의 그림처럼 참조를 하게 된다. `doSomeInstancing.foo`같은 경우는 `prototype chain`을 타고 가서 `doSomething`의 `prototype`을 참조하게 되어 bar가 출력되게 된다. 헷갈렸던 부분은 `doSomething.foo`이었는데 그림처럼 `doSomething`은 `function`을 참조할 뿐이어서 `function`에는 `foo` 속성이 없어서 `undefined`가 뜨게 된다.

![prototype_and_instance2](https://user-images.githubusercontent.com/11348329/77530169-45b78a80-6ed4-11ea-990d-01459ca78eda.jpg)

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

### 2-1. john.[[Prototype]] = Human.prototype?
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
```js
let Human = function(name) {
  this.name = name;
}
Human.prototype.sleep = function() {
  console.log(this.name + ' is sleeping...');
};

let steve = new Human('steve');

let Student = function(name) {
  Human.call(this, name);
}
Student.prototype = Object.create(Human.prototype);
Student.prototype.constructor = Student;
Student.prototype.sleep = function() {
  //Human.prototype.sleep.apply(this); // Human의 sleep함수를 이용하고 싶을 때
  console.log('Students never sleep.');
}
Student.prototype.learn = function() {
  console.log(this.name + ' is learning something...');
};

let john = new Student('john');
john.learn();
john.sleep();
steve.sleep();
```


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
    // super.sleep(); //Human의 sleep함수를 이용하고 싶을 때
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

출처  
Codestates Immersive Course
[mdn 상속과 프로토타입]  

[mdn 상속과 프로토타입]: https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Inheritance_and_the_prototype_chain
