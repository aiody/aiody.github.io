---
title: "[공부 기록] Data Structure - Stack and Queue"
date: 2020-03-19 14:32:00
categories: JavaScript DataStructure
---

## Queue
`Queue`는 가장 처음 들어간 데이터가 가장 먼저 나오는 구조이다. (FIFO: first in, first out)  
파이프를 생각하면 쉽다. 아래의 그림처럼 파이프에 빨강, 노랑, 초록 순으로 공을 넣는다고 하자.  
// 그림 넣음.
그렇다면 가장 먼저 나오게 되는 공은 가장 처음 넣은 빨간 공이다. 같은 논리로 빨강, 노랑, 초록 순으로 공이 빠져나오게 되는 것이다.  
// 빠져나온 그림.
이러한 자료 구조를 `Queue`라고 한다.

### Queue의 구성
|내용|설명|
|---|---|
|enqueue()|큐에 데이터를 추가한다.|
|dequeue()|큐에 데이터를 꺼낸다.|
|init()|큐를 초기화 한다.|
|is_empty()|큐가 비어있는지 알아낸다.|
|size()|큐에 들어있는 데이터의 개수를 얻는다.|
|Front|맨 앞에 있는 데이터를 가리킨다.|
|Rear|맨 뒤에 있는 데이터를 가리킨다.|

### Queue를 어떤 논리로 구현할 수 있을까? (pseudo code)
```js
let queue = [];
let front = 0;
let rear = 0;

function init() {
  front = 0;
  rear = 0;
  queue = [];
}

function enqueue(데이터) {
  // queue에 rear위치에 데이터를 넣는다.
  // rear 값을 하나 증가시킨다.
}

function dequeue() {
  // queue의 front위치에 있는 데이터를 리턴한다.
  // front값을 하나 증가시킨다.
}

function is_empty() {
  // front와 rear의 값이 같으면 비어있다.
}

function size() {
  // rear - front를 리턴한다.
}
```

## Stack
`Stack`은 가장 나중에 들어간 데이터가 가장 먼저 나오는 구조이다. (LIFO: last in, first out)  
한 쪽이 막힌 파이프를 생각하면 된다. 똑같이 빨강, 노랑, 초록 순으로 공을 넣어보자.  
// 그림 넣음.
파이프 한 쪽이 막혀있기 때문에 가장 마지막에 넣은 초록 공이 제일 먼저 나오게 된다. 결국 초록, 노랑, 빨강 순으로 공이 빠져나오게 된다.  
// 빠져나온 그림.
이러한 자료 구조를 `Stack`이라고 한다.

### Stack의 구성
|내용|설명|
|---|---|
|push()|스택에 데이터를 추가한다.|
|pop()|스택에 데이터를 꺼낸다.|
|init()|스택을 초기화 한다.|
|is_empty()|스택이 비어있는지 알아낸다.|
|size()|스택에 들어있는 데이터의 개수를 얻는다.|
|Top|가장 최근에 입력된 데이터를 가리킨다.|

### Stack을 어떤 논리로 구현할 수 있을까? (pseudo code)
```js
let stack = [];
let top = -1;

function init() {
  stack = [];
  top = -1;
}

function push(데이터) {
  // top의 값을 하나 증가시킨다.
  // stack의 top위치에 데이터를 넣는다.
}

function pop() {
  // stack의 top위치에 데이터를 리턴한다.
  // top의 값을 하나 감소시킨다.
}

function is_empty() {
  // top이 -1이면 비어있다.
}

function size() {
  // top + 1를 리턴한다.
}
```

출처  
<https://www.tutorialride.com/data-structures/queue-in-data-structure.htm>  
<https://www.tutorialride.com/data-structures/stack-in-data-structure.htm>  
