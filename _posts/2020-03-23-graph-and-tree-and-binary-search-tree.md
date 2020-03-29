---
title: "[공부 기록] Data Structure - Graph and Tree and Binary Search Tree"
date: 2020-03-23 13:04:00
categories: DataStructure
---

## Graph
`Graph`는 여러 개의 노드와 그 노드들을 연결짓는 선으로 구성된 자료 구조이다. 
![Graph_basic](https://user-images.githubusercontent.com/11348329/77285099-97fd7d80-6d13-11ea-967b-fbde820263b6.jpg)


### Graph의 종류
![directed_undirected_graph](https://user-images.githubusercontent.com/11348329/77285101-992eaa80-6d13-11ea-9c44-8f5c236ff31b.jpg)
선의 종류에 따라 `Directed Graph`와 `Undirected Graph`로 나뉠 수 있다.  
`Directed Graph`에서 노드가 자기 스스로와 연결된 선을 가질 때 그것을 `Self edge`라고 부른다.
![cyclic_acyclic_graph](https://user-images.githubusercontent.com/11348329/77285102-99c74100-6d13-11ea-8d7c-13ef12531b13.jpg)
`Graph` 내부에서 순환이 있을 경우 `Cyclic graph`라고 부르고 순환이 없을 경우 `Acyclic graph`라고 부른다.
![weighted_graph](https://user-images.githubusercontent.com/11348329/77285104-9a5fd780-6d13-11ea-9ce1-df63478812ee.jpg)
`edge`에 가중치가 붙은 경우 `Weighted graph`라고 부른다.
![connected_disconnected_graph](https://user-images.githubusercontent.com/11348329/77285105-9af86e00-6d13-11ea-8300-27acd30dac3d.jpg)
연결되어 있는 그래프를 `connected graph`라고 하고 따로 떨어져 있는 그래프를 `disconnected graph`라고 부른다.
![complete_graph](https://user-images.githubusercontent.com/11348329/77285108-9b910480-6d13-11ea-8cff-2122b6de0f61.jpg)
각 노드끼리 모두 연결되어 있으면 `complete graph`라고 부른다.

### Graph를 표현하는 방법
![adjacency_matrix](https://user-images.githubusercontent.com/11348329/77285106-9b910480-6d13-11ea-83e8-641943976ba9.jpg)
Adjacency Matrix : 2차원 배열
![adjacency_list](https://user-images.githubusercontent.com/11348329/77285109-9cc23180-6d13-11ea-8b8b-14f3d700cb0e.jpg)
Adjacency List : Linked list

### Graph의 탐색
DFS(depth-first search) 깊이 우선 탐색 : 노드에서 가장 깊은 곳까지 탐색 후 다음 넓이를 검사하는 방식.  
BFS(breadth-first search) 너비 우선 탐색 : 노드에서 갈 수 있는 넓이를 모두 탐색 후 다음 깊이를 검사하는 방식.

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
![pseudocode_of_graph](https://user-images.githubusercontent.com/11348329/77825382-45292900-714c-11ea-8d9f-ce9be070cb1f.jpg)

## Tree
`Tree`는 노드들 간의 계층이 있어서 부모와 자식이 존재하는 자료 구조이다. 
`Root node`는 자식을 0개 이상 갖고 있고 그 자식들도 자식을 가지고 있는 `Tree` 안에 `Tree`가 존재하는 모양새이다.
크게 보았을 때 `Tree`는 `Graph`의 한 부분이라고 볼 수 있다. Directed Acylic Graph(방향성이 없는 비순환 그래프)라고 볼 수 있다.
![Tree_basic](https://user-images.githubusercontent.com/11348329/77285622-c3cd3300-6d14-11ea-8332-fc098af6cffb.png)


### Tree의 종류
![binary_tree_and_binary_search_tree](https://user-images.githubusercontent.com/11348329/77286514-c0d34200-6d16-11ea-9095-ab53948430ad.jpg)
Binary Tree - 자식을 최대 두 개 까지만 갖는 `Tree`  
Binary Search Tree - 특정한 규칙에 따라 값들이 정렬되어 있는 `Tree`  
![balanced_and_unbalanced_binary_tree](https://user-images.githubusercontent.com/11348329/77286516-c2046f00-6d16-11ea-9d09-4ed8e42a32db.jpg)
Balanced Tree - 노드들이 균형있게 자리 잡혀있는 `Tree`  
Unbalanced Tree - 노드들이 지나치게 치우쳐있는 `Tree`  
![complete_binary_tree](https://user-images.githubusercontent.com/11348329/77286519-c29d0580-6d16-11ea-9e16-dfb25144fabc.jpg)
Complete Binary Tree - 이진 트리 중 모든 노드들이 레벨별로 왼쪽부터 채워져있으면 완전 이진 트리.  
![full_and_perfect_binary_tree](https://user-images.githubusercontent.com/11348329/77286521-c3359c00-6d16-11ea-93ab-6f9398fd7882.jpg)
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
![pseudo_code_of_tree](https://user-images.githubusercontent.com/11348329/77845486-427d1100-71ea-11ea-808e-cb47e9ddda29.jpg)

## Binary Search Tree
![binary_search_tree](https://user-images.githubusercontent.com/11348329/77286523-c3ce3280-6d16-11ea-8fa6-629f526add27.jpg)

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
![pseudo_code_of_binary_search_tree](https://user-images.githubusercontent.com/11348329/77845487-43ae3e00-71ea-11ea-989a-6d2f21064557.jpg)

출처  
Graph
<https://youtu.be/fVcKN42YXXI>  
<https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html>  
Tree
<https://youtu.be/LnxEBW29DOw>  
<https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html>  

