---
title: "[공부 기록] JavaScript - Array functions"
date: 2020-03-29 19:42:00
categories: JavaScript
---
JavaScript에서 Array를 쓰면서 익숙해지지 않은 함수들을 모아서 정리해보았다.

## 1. concat
concat은 두 개 이상의 배열을 합쳐주는 함수이다. 매개변수로 배열을 받고 기존의 배열은 변경시키지 않고 합쳐진 결과만을 리턴한다.

### 1-1. 배열 두 개를 합칠 때
```js
const letters = ['a', 'b', 'c'];
const numbers = [1, 2, 3];

letters.concat(numbers);
// result in ['a', 'b', 'c', 1, 2, 3]
```

### 1-2. 배열 세 개를 합칠 때
```js
const num1 = [1, 2, 3];
const num2 = [4, 5, 6];
const num3 = [7, 8, 9];

const numbers = num1.concat(num2, num3);

console.log(numbers); 
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 1-2. 값과 배열을 합칠 때
```js
const letters = ['a', 'b', 'c'];

const alphaNumeric = letters.concat(1, [2, 3]);

console.log(alphaNumeric); 
// results in ['a', 'b', 'c', 1, 2, 3]
```

### 1-3. 포개어진 배열을 합칠 때
```js
const num1 = [[1]];
const num2 = [2, [3]];

const numbers = num1.concat(num2);

console.log(numbers);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(numbers);
// results in [[1, 4], 2, [3]]
```

## 2. splice
splice는 배열 내의 요소를 제거하거나 덮어씀으로써 값을 변경하는 함수이다. 첫 번째 매개변수로 배열의 변경할 시작 인덱스를 받는다. 두 번째 매개변수로는 삭제할 요소의 수를 받는다. 세 번째 매개변수는 배열에 추가할 요소이고 입력하지 않으면 삭제만을 진행한다. 최종적으로 값이 변경 된 배열을 리턴한다.  

### 2-1. 하나도 제거하지 않고 요소 1개 추가하기
```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum');

// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"] 
// removed is [], no elements removed
```
### 2-2. 하나도 제거하지 않고 요소 2개 추가하기
```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum', 'guitar');

// myFish is ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"] 
// removed is [], no elements removed
```
### 2-3. 1개 요소 제거하기
```js
var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
var removed = myFish.splice(3, 1);

// removed is ["mandarin"]
// myFish is ["angel", "clown", "drum", "sturgeon"] 
```
### 2-4. 1개 요소 제거하고 1개 추가하기
```js
var myFish = ['angel', 'clown', 'drum', 'sturgeon'];
var removed = myFish.splice(2, 1, 'trumpet');

// myFish is ["angel", "clown", "trumpet", "sturgeon"]
// removed is ["drum"]
```
### 2-5. 시작 인덱스부터 모두 제거하기
```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2);

// myFish is ["angel", "clown"] 
// removed is ["mandarin", "sturgeon"]
```

## 3. forEach
forEach는 배열의 각 요소마다 매개변수로 넘겨지는 function을 실행하는 함수이다.
```js
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```
## 4. reverse
reverse는 배열을 거꾸로 배치해주는 함수이다. 기존의 배열의 값이 바뀌기 때문에 주의해서 써야한다.
```js
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]
```
## 5. join
join은 배열의 각 요소를 모아서 한 문자열로 만들어주는 함수이다. 매개변수로 어떤 문자를 넣으면 요소 사이에 넣어서 만들어주게 된다.
```js
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join());
// expected output: "Fire,Air,Water"

console.log(elements.join(''));
// expected output: "FireAirWater"

console.log(elements.join('-'));
// expected output: "Fire-Air-Water"
```

출처  
[mdn Array.prototype.cancat()]  
[mdn Array.prototype.splice()]  
[mdn Array.prototype.forEach()]  
[mdn Array.prototype.reverse()]  
[mdn Array.prototype.join()]  

[mdn Array.prototype.cancat()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat
[mdn Array.prototype.splice()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
[mdn Array.prototype.forEach()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach
[mdn Array.prototype.reverse()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse
[mdn Array.prototype.join()]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join
