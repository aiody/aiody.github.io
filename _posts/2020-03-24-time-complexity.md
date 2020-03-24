---
title: "[공부 기록] Data Structure - Time Complexity"
date: 2020-03-24 16:15:00
categories: DataStructure
---

## Time Complexity란?
`Time Complexity`(시간 복잡도)란 알고리즘을 실행할 때 시간이 얼마나 걸릴지 나타내는 것이다.
`Time Complexity` 표기법에는 아래와 같이 세 가지 방법이 있다.  
최상의 경우 : 오메가 표기법 (Big-Ω Notation)  
평균의 경우 : 세타 표기법 (Big-θ Notation)  
최악의 경우 : 빅오 표기법 (Big-O Notation)  

여기서 Big-O 표기법을 주로 사용하는데 이에 대해서 알아보자.

## Big-O란?
`Big-O` 표기법은 알고리즘을 실행할 때 최악의 경우를 표시한 것이다. 이는 알고리즘에서 불필요한 연산을 제거하려는 목적이 있다. 아래의 그림은 대표적인 Big-O의 복잡도를 나타내는 그림이다.
![Big-O_notation](https://user-images.githubusercontent.com/11348329/77415258-91e7c980-6e05-11ea-8432-3766bc43948e.jpg)
![time_complexity](https://user-images.githubusercontent.com/11348329/77415257-90b69c80-6e05-11ea-9755-b4c0a6215cc4.jpg)

## 자료구조별 Time Complexity 분석
### Array
**Lookup** : index로 바로 참조하면 되기 때문에 O(1) - Constant.  
**Assign** : index로 바로 참조하여 값을 넣으면 되기 때문에 O(1) - Constant.  
**Insert** : 값을 넣기 위해서는 뒤에 있는 값을 한 칸씩 뒤로 이동해야 하기 때문에 최악의 경우(맨 앞에 값을 넣는 경우) O(n) - Linear.  
**Remove** : 값을 지우고 뒤에 있는 값을 한 칸씩 앞으로 옮겨야 하기 때문에 최악의 경우(맨 앞에 값을 넣는 경우) O(n) - Linear.  
**Find** : `Array`에 있는 모든 값을 찾아야 하기 때문에 O(n) - Linear.  

### Linked List
**Lookup** : `Head`부터 해당 번째에 있는 값을 순차적으로 찾아야 하기 때문에 O(n) - Linear.  
**Find** : `Head`부터 해당 값이 있는 곳까지 순차적으로 찾아야 하기 때문에 O(n) - Linear.  
**Assign** : `Head`부터 해당 값이 있는 곳까지 순차적으로 찾아서 변경해야 하기 때문에 O(n) - Linear.  
**Insert** : 추가하고 싶은 곳의 위치를 아는 경우(탐색이 끝난 경우) 노드를 생성하고 연결만 해주면 되기 때문에 O(1) - Constant.  
**Remove** : 지우고 싶은 곳의 앞 노드까지 탐색해야 하기 때문에 O(n) - Linear. 만약 지우고 싶은 곳의 앞 노드를 알거나 맨 앞 노드를 지운다면 O(1) - Constant.  
### Doubly Linked List
**Lookup, Find, Assign, Insert**는 `Linked List`와 같음.  
**Remove** : 지우고 싶은 곳의 위치를 아는 경우(탐색이 끝난 경우), 양방향 연결이기 때문에 앞 노드를 알 수 있어서 O(1) - Constant.  
### Tree
**Find** : 모든 child를 찾아야 하기 때문에 O(n) - Linear.  
### Binary Search Tree
**Find, Insert, Remove** : 일반적으로 현재 노드보다 작은 값은 왼쪽, 현재 노드보다 큰 값은 오른쪽에 정렬되어 있기 때문에 모든 노드를 탐색할 필요가 없다. 그래서 `Binary Search Tree`의 높이를 h라고 했을 때 O(h)만큼 걸리는데 일반적으로 `Binary Search Tree`의 높이는 log 2n이기 때문에 O(log n) - logarithmic.  
그러나 데이터가 고르게 분포되어 있지 않고 한 쪽에 쏠려있는 경우는 결국 모든 노드를 찾아야 하기 때문에 O(n) - Linear. 이를 해결하기 위해 노드를 추가할 때마다 균형에 맞도록 재배치해야 한다.  
### Hash Table
**Find, Insert, Remove** : 해시 함수의 시간복잡도는 고려하지 않기 때문에 이미 할당된 배열에 index로 접근하면 되기 때문에 O(1) - Constant. 최악의 경우(해시 충돌이 일어난 경우) Bucket에 들어있는 값을 모두 확인해야 하기 때문에 O(n) - Linear.  



출처  
<https://blog.chulgil.me/algorithm/>  
<https://velog.io/@cyranocoding/Hash-Hashing-Hash-Table%ED%95%B4%EC%8B%9C-%ED%95%B4%EC%8B%B1-%ED%95%B4%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0%EC%9D%98-%EC%9D%B4%ED%95%B4-6ijyonph6o>  
<https://mattlee.tistory.com/30>  

