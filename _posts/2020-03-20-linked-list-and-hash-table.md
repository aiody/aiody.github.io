---
title: "[공부 기록] Data Structure - Linked list and Hash table"
date: 2020-03-20 13:04:00
categories: DataStructure
---

## Linked list
`Linked list`는 크게 두 부분으로 나뉘어 있는 노드(객체)들의 연결 집합이다. 각 노드들은 값을 갖는 부분과 다음 노드의 주소를 갖는 두 부분으로 이루어져있다.  
![linked_list_node](https://user-images.githubusercontent.com/11348329/77137338-cd566100-6ab0-11ea-9463-dabcb36811f6.jpg)
<center> <노드 한 개의 구조> </center>  

여러 노드들을 연결하면 `Linked list`가 되는데 `Header`가 가리키는 노드는 첫 번째 노드가 되고 Null을 가리키는 노드는 마지막 노드가 된다.  
![simple_linked_list](https://user-images.githubusercontent.com/11348329/77137342-ce878e00-6ab0-11ea-897a-5b8e2b84ec77.jpg)
<연결된 노드들의 구조>

이러한 자료 구조를 `Linked list`라고 한다. 엄밀히 말하자면 `Simple linked list`(단순 연결 리스트)이다.  
다양한 종류가 더 있지만 이 포스트에서는 `Simple linked list`만 다룰 것이다.

### Linked list의 구성
| 내용 | 설명 |
| -------- | -------- |
| head | 맨 앞의 노드를 가리킨다. |
| tail | 맨 뒤의 노드를 가리킨다. |
| addToTail() | 맨 앞에 노드를 추가한다. |
| removeHead() | 맨 뒤의 노드를 삭제한다. |
| contains() | 특정한 값을 가진 노드가 있는지 검사한다. |

### Linked list를 어떤 논리로 구현할 수 있을까? (pseudo code)
![pseudo_code_linked_list](https://user-images.githubusercontent.com/11348329/77138987-87e96200-6ab7-11ea-8853-4f5aceaf5fb5.jpg)

## Hash table
(작성중)

### Hash table의 구성
(작성중)

### Hash table을 어떤 논리로 구현할 수 있을까? (pseudo code)
(작성중)

출처  
<https://hyeonstorage.tistory.com/259>  
