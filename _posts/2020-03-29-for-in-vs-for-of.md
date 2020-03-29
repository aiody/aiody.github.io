---
title: "[공부 기록] JavaScript - for...in과 for...of의 차이점"
date: 2020-03-29 20:40:00
categories: JavaScript
---
공부를 하다가 `for...in`과 `for...of`의 차이점에 대하여 궁금해서 정리하게 되었다.

간단히 얘기해서 `for...in`은 `enumerable properties`를 반복(iterate)하고 `for...of`은 `iterable object`만을 반복한다.  
`enumerable properties`은 뜻을 해석하면 열거 가능한 속성들이고 이는 `Object.getOwnPropertyDescriptor()`로부터 확인할 수 있다.  
`iterable object`는 `Symbol.iterator` 속성을 가지고 있는 오브젝트들인데 예를 들어 `Array`, `Map` 등이 있다.  
`for...in`는 key값만 가지고 올 수 있고 value값은 가져올 수 없다.

```js
Object.prototype.objCustom = function() {}; 
Array.prototype.arrCustom = function() {};

const iterable = [3, 5, 7];
iterable.foo = 'hello';

for (const i in iterable) {
  console.log(i); // logs 0, 1, 2, "foo", "arrCustom", "objCustom"
}

for (const i in iterable) {
  if (iterable.hasOwnProperty(i)) {
    console.log(i); // logs 0, 1, 2, "foo"
  }
}

for (const i of iterable) {
  console.log(i); // logs 3, 5, 7
}
```
여기서 Array는 Object를 상속받았기 때문에 `iterable`은 `foo`뿐만 아니라 `arrCustom`과 `objCustom`에 모두 접근할 수 있다. 그래서 `for...in` 구문에서 `iterable`의 key값, 즉 index값을 모두 출력하고도 `foo`, `arrCustom`, `objCustom`을 모두 출력한다.  
반면에 `for...of`구문은 `iterable object`만 반복하기 때문에 `iterable`의 값만 출력하게 되었다.  


출처  
[mdn for...of]  
https://stackoverflow.com/questions/29285897/what-is-the-difference-between-for-in-and-for-of-statements-in-jav  
https://jsdev.kr/t/for-in-vs-for-of/2938  
https://im-developer.tistory.com/139  

[mdn for...of]: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...of
