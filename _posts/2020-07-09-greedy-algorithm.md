---
title: "Greedy Algorithm(그리디/탐욕 알고리즘)"
date: 2020-07-09 18:37:00
categories: Algorithm
---

## 1. 그리디 알고리즘이란?
매 선택에서 지금 이 순간 당장 최적인 답을 선택하여 적합한 결과를 도출하는 알고리즘.  

## 2. 어떤 경우에 사용하는가?
1. 앞의 선택이 이후 선택에 영향을 주지 않을 때
2. 문제 전체에 대한 최적해가 부분 문제에 대해서도 역시 최적해가 될 때

위의 두 조건을 만족하면 그리디 알고리즘으로 풀어도 됩니다.  
그리디 알고리즘을 쓰는 문제는 뭔가를 가장 빨리~, 가장 큰~ 이라는 단어가 많이 들어갑니다. 문제를 보고 `완전탐색`으로 풀기에는 경우의 수가 큰데, 뒷일은 생각하지 않고 각 단계에서 최선을 택해도 정답을 구할 수 있을 것 같을 때 그리디 알고리즘을 사용하면 됩니다.  

## 3. 어떻게 사용하는가?
여러 경우 중 하나를 선택할 때 그것이 그 상황에서 가장 좋다고 생각하는 것을 선택해 나가는 방식으로 진행하여 답을 구합니다.  
그 상황에서 가장 좋다고 생각하는 것을 선택해 나가는 방식이기 때문에 가장 좋은 결과를 얻는 것이 보장되는 것은 아닙니다.  

## 4. 대표적인 문제
ATM : <https://www.acmicpc.net/problem/11399>  
동전0 : <https://www.acmicpc.net/problem/11047>  
회의실배정 : <https://www.acmicpc.net/problem/1931>  

출처  
<https://ratsgo.github.io/data%20structure&algorithm/2017/11/22/greedy/>  
<https://namu.wiki/w/그리디%20알고리즘>  
<https://janghw.tistory.com/entry/알고리즘-Greedy-Algorithm-탐욕-알고리즘>  
<https://foxtrotin.tistory.com/91>  
