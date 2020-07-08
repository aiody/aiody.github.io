---
title: "[공부 기록] 4주 프로젝트 완료 및 후기"
date: 2020-07-07 15:18:00
categories: Project
---

Codestates에서의 4주간의 마지막 프로젝트가 끝이 났다. 지금이 아니면 정리를 못하고 넘어갈 것 같아서 프로젝트 중에 썼던 노션 페이지를 참고하여 정리하려고 한다.  
총 4명이서 프로젝트를 진행했고 3명의 프론트엔드와 나는 백엔드를 맡아서 4주간 진행했다. git 환경이었고 매일 오전 10시에 스탠드업 미팅과 오후 5시에 코드리뷰를 했다.  
커밋 메시지를 자세히 쓰는 것과 풀리퀘스트를 머지하기 전에 팀원들의 리뷰가 필수라는 것 그리고 오랫동안 고민할 경우에 팀원들의 도움을 적극적으로 받는다는 팀 규칙이 있었다.  

## 1. 프로젝트 소개

### 1-1. 개요
우연히 심리상담소를 추천해 달라는 글을 보게 되었는데 나도 심리 상담에 관심이 있어서 추천하는 [링크]에 들어가 보았다. 그 링크는 네이버 블로그였고 블로그 주인이 댓글로 추천을 받고 추천 받은 심리상담소를 구글 지도에 저장해서 공유하는 방식으로 되어있었다. 아주 좋은 취지의 블로그였지만 블로그 주인이 손수 댓글을 확인하고 지도를 작성하는게 불편해보였다. 막연히 개발자로서 '생각보다 많은 사람들이 이런 서비스를 원하는 구나', '이런 서비스가 어플로 있다면 정말 편할텐데'라고만 생각하고 넘겼었다.  
4주짜리 프로젝트를 기획 단계에 있을 때 예전에 생각해뒀던 이 아이디어가 떠올라서 심리상담소를 추천해주는 지도 어플리케이션을 만들게 되었다.  

### 1-2. 주요 기능
- 회원가입  
  - 회원가입 기능이다. 유저로서 그리고 센터(심리상담소/정신과)로서 회원가입할 수 있다.  
- 관심사 조사(유저), 전문 분야 조사(센터)  
  - 회원가입 이후에 바로 진행되는 단계이다.  
  유저는 관심사를 조사하게 되는데 어떤 분야에서 치료받고 싶은지, 어떤 지역이 편한지, 심리상담소와 정신과 둘 중 어떤 곳을 가고 싶은지 조사한다. 이 정보를 바탕으로 지도에 추천하는 심리센터를 표시하게 된다.  
  센터 쪽은 그 센터가 어떤 분야를 전문적으로 치료하는지 조사한다.  
- 로그인/로그아웃  
  - 기본적인 로그인, 로그아웃 기능이다.  
- 지도 기능  
  - 기본적인 지도 기능이다. 이동, 확대/축소, 회전, 현위치로 돌아가기 기능이 가능하다.  
- 검색 기능  
  - 심리센터를 검색할 수 있다. 현재 위치에서 검색, 위치로 검색, 이름으로 검색 세 가지 방법으로 검색할 수 있다.  
- 필터 기능  
  - 관심 분야 혹은 선호하는 센터 종류(심리상담소/정신과)로 필터링해서 센터를 지도에 보여줄 수 있다.  
- 상세페이지  
  - 지도 위의 마커를 눌렀을 때 심리상담소의 정보를 자세히 보여주는 페이지이다. 즐겨찾기, 전화, 리뷰보기, 예약하기 기능이 있다.  
- 마이페이지  
  - 관심사 수정, 예약 관리, 리뷰 관리, 로그아웃을 할 수 있는 페이지이다.  
- 센터 어드민
  - 센터 계정으로 로그인하면 볼 수 있다. 메인 페이지에는 별점 그래프와 리뷰를 확인할 수 있고 회원가입할 때 등록했던 전문 분야를 수정할 수 있다. 예약 관리 페이지에는 이 상담소로 등록된 예약을 관리할 수 있다.  

### 1-3. 기술 Stack
프로젝트를 진행하며 사용한 기술 스택이다.
![behappy_tech_stack](https://user-images.githubusercontent.com/11348329/86929877-4fa68600-c171-11ea-9516-955d4b4ea769.png)

### 1-4. Flow
프로젝트 시작 전에 미리 설계한 Flow이다.
![behappy_flow_1](https://user-images.githubusercontent.com/11348329/86929469-dad34c00-c170-11ea-8152-de9b474c1d73.jpg)
![behappy_flow_2](https://user-images.githubusercontent.com/11348329/86929465-da3ab580-c170-11ea-8bf1-28254ba361a1.jpg)
![behappy_flow_3](https://user-images.githubusercontent.com/11348329/86929459-d7d85b80-c170-11ea-83c3-770f89ab82be.jpg)
![behappy_flow_4](https://user-images.githubusercontent.com/11348329/86929463-da3ab580-c170-11ea-9ce5-71c3a7274c2a.jpg)

### 1-5. Navigation Design
프로젝트 시작 전에 설계한 네비게이션이다.
![behappy_navigation_design_1](https://user-images.githubusercontent.com/11348329/86930095-909e9a80-c171-11ea-9d8a-4a053dbb004a.jpg)
![behappy_navigation_design_2](https://user-images.githubusercontent.com/11348329/86930101-92685e00-c171-11ea-96de-e05afa72ea3e.jpg)
![behappy_navigation_design_3](https://user-images.githubusercontent.com/11348329/86930102-9300f480-c171-11ea-9828-827a8ec87bd8.jpg)

### 1-6. Schema
프로젝트를 시작 전에 큰 틀을 설계해뒀다가 중간에 수정이 있어서 마지막 버전의 데이터 스키마이다.
![behappy_data_schema](https://user-images.githubusercontent.com/11348329/86930269-ccd1fb00-c171-11ea-9cd1-1d2af4c2d8f2.png)

## 2. 완성

[BeHappy APK 다운로드]

### 2-1. 기능별 시연 영상

#### 회원가입(유저), 관심사 조사, 로그인
{ % youtube https://youtu.be/JZx7UbzWpHU % }
#### 현재 위치에서 검색, 위치로 검색, 이름으로 검색, 현위치로 돌아가기
{ % youtube https://youtu.be/wUjwnGKi2Og % }
#### 관심분야와 선호하는 센터로 필터링
{ % youtube https://youtu.be/KUPhwcrp9F0 % }
#### 관심사를 수정했을 때 추천하는 마커가 바뀌는 것
{ % youtube https://youtu.be/FG89Lx83txM % }
#### 마커를 눌렀을 때 나오는 상세페이지 및 예약하기
{ % youtube https://youtu.be/v6PWUxVHGCY % }
#### 즐겨찾기 추가/삭제
{ % youtube https://youtu.be/ase-zRUrq7k % }
#### [마이페이지] 예약 관리 - 예약 수정/삭제, 리뷰 작성
{ % youtube https://youtu.be/ZYwWBHygbW8 % }
#### [마이페이지] 리뷰 관리 - 리뷰 수정/삭제
{ % youtube https://youtu.be/erq5tYGQhhY % }
#### 유저 로그아웃, 센터(심리상담소/정신과) 회원가입 및 로그인
{ % youtube https://youtu.be/HUadmwJDpFY % }
#### 슈퍼 어드민(웹) - 센터 admin 가입 수락/거절
![adminRequest](https://user-images.githubusercontent.com/11348329/86935462-d2324400-c177-11ea-9170-09ca8ca9c1f9.gif)
#### [센터페이지] 메인 - 별점 그래프, 리뷰, 전문분야 수정
{ % youtube https://youtu.be/EspbY0SzoTU % }
#### [센터페이지] 예약 관리 - 진료 완료/미완료
{ % youtube https://youtu.be/0_v2xpdkOGw % }

### 2-2. repositories
server : https://github.com/aiody/BeHappy-server.git  
client : https://github.com/aiody/BeHappy-client.git  

## 3. 후기
2주 프로젝트 때와 마찬가지로 기획 단계에서 Flow와 데이터 스키마, 네비게이션 설계를 잘 해두니 설계 단계에서는 정말 고통스러웠지만 프로젝트를 진행할 때 작업이 정말 수월했다. 프로젝트 후반에 시간이 남아서 도커로 컨테이너를 만들어서 서버를 로드밸런싱도 해보고 원래는 계획에 없었던 배포도 진행해보았다. 다음에는 젠킨스와 연동해서 꼭 자동 배포를 도전해볼 것이다. 정말 기대된다.  


[링크]: https://m.blog.naver.com/leeojsh/220852877049 
[BeHappy APK 다운로드]: https://expo.io/artifacts/7ce77196-f809-447a-a82b-a4a5651567f6
