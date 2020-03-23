---
title: "[공부 기록] Data Structure - Graph and Tree and Binary Search Tree"
date: 2020-03-23 13:04:00
categories: DataStructure
---

## Graph
`Graph`는 여러 개의 노드와 그 노드들을 연결짓는 선으로 구성된 자료 구조이다. 

// 일반적인 그래프 그림 - 노드, 에지 알려주기
예> 도로, 지하철 노선도의 최단 경로


### Graph의 종류
선의 종류에 따라 `Directed Graph`와 `Undirected Graph`로 나뉠 수 있다.  
`Directed Graph`에서 노드가 자기 스스로와 연결된 선을 가질 때 그것을 `Self edge`라고 부른다.
`Graph` 내부에서 순환이 있을 경우 `Cyclic graph`라고 부르고 순환이 없을 경우 `Acyclic graph`라고 부른다.
// 그림 directed graph, unditected graph, self edge
// 그림 cyclic, acyclic
// Weighted graph
// connected graph / disconnected graph
// complete graph

### Graph를 표현하는 방법
Adjacency Matrix : 2차원 배열
Adjacency List : Linked list

// adjacency matrix
// adjacency list 그림

### Graph의 탐색
깊이 우선 탐색 DFS depth first search 너비 우선 탐색 BFS breadth first search

### Graph의 구성
| 내용 | 설명 |
| -------- | -------- |
| addNode() | 노드를 추가한다. |
| removeNode() | 노드를 삭제한다. |
| addEdge() | 간선을 추가한다. |
| removeEdge() | 간선을 삭제한다. |
| contains() | 특정한 노드가 있는지 검사한다. |
| hasEdge() | 특정한 노드가 간선이 연결되어 있는지 검사한다. |

### Graph를 어떤 논리로 구현할 수 있을까? (pseudo code)
(작성중)

## Tree
`Tree`는 노드들 간의 계층이 있어서 부모와 자식이 존재하는 자료 구조이다. 
`Root node`는 자식을 0개 이상 갖고 있고 그 자식들도 자식을 가지고 있는 `Tree` 안에 `Tree`가 존재하는 모양새이다.
크게 보았을 때 `Tree`는 `Graph`의 한 부분이라고 볼 수 있다. Directed Acylic Graph(방향성이 없는 비순환 그래프)라고 볼 수 있다.

// 일반적인 트리 그림 - leaf 포함, root node

### Tree의 종류
Binary Tree - 자식을 최대 두 개 까지만 갖는 `Tree`
Binary Search Tree - 특정한 규칙에 따라 값들이 정렬되어 있는 `Tree`
Balanced Tree - 노드들이 균형있게 자리 잡혀있는 `Tree`
Unbalanced Tree - 노드들이 지나치게 치우쳐있는 `Tree`
Complete Binary Tree - 이진 트리 중 모든 노드들이 레벨별로 왼쪽부터 채워져있으면 완전 이진 트리.
Full Binary Tree - 자식을 하나만 가진 노드가 없을 때 즉 자식을 하나도 가지고 있지 않거나 두 개를 가졌을 때 전 이진 트리라고 한다.
Perfect Binary Tree - 모든 말단 노드가 같은 레벨에 있고 모든 노드가 두 개의 자식을 가지고 있을 때 포화 이진 트리라고 한다.

### Tree의 구성
| 내용 | 설명 |
| -------- | -------- |
| value | 현재 노드가 가진 값. |
| children | 현재 노드에 붙어 있는 자식들. |
| addChild() | 자식 노드를 추가하기. |
| contains() | Tree에 특정 값을 가지고 있는지 검사하기. |

### Tree를 어떤 논리로 구현할 수 있을까? (pseudo code)
(작성중)

## Binary Search Tree
`Binary Tree`의 한 종류라고 볼 수 있으며 현재 노드보다 왼쪽에 있는 값이 더 작고 현재 노드보다 오른쪽에 있는 값이 더 크게 정렬된 트리를 `Binary Search Tree`라고 한다.

### Binary Search Tree의 구성
| 내용 | 설명 |
| -------- | -------- |
| value | 현재 노드가 가진 값. |
| left | 현재 노드의 왼쪽 자식. |
| right | 현재 노드의 오른쪽 자식. |
| insert() | Binary Search Tree에 값을 넣기. |
| contains() | Binary Search Tree에 특정 값을 가지고 있는지 찾기. |
| depthFirstLog() | DFS를 통해 탐색한 순서대로 로그 출력하기. |

### Binary Search Tree를 어떤 논리로 구현할 수 있을까? (pseudo code)
(작성중)

출처  
Graph
<https://youtu.be/fVcKN42YXXI>  
<https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html>  
Tree
<https://youtu.be/LnxEBW29DOw>  
<https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html>  

