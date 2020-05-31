---
title: "[공부 기록] 첫 2주짜리 프로젝트"
date: 2020-05-31 21:29:00
categories: Project
---

Codestates에서의 2주짜리 첫 프로젝트를 마무리하였다.  
나는 팀장을 맡고 3명의 팀원들과 함께 2주동안 열심히 달렸다.  
주로 백엔드를 작업했지만 막바지에 프론트엔드를 도와서 작업했다.  

## 1. 프로젝트 소개

### 1-1. 개요
평소에 에너지가 적은 사람이여서 내 작은 몸뚱이 하나를 이끄는 것을 힘들어하는 편이다. 그것을 극복하고자 생산적인 일들을 습관으로 만듦으로써 적은 에너지로 뿌듯한 하루를 만든다. 그럴 때 유용하게 쓰는 것이 습관을 관리해주는 어플이다. 이런 어플들을 사용하면서 느꼈던 불만 중 하나는 내가 필요한 기능을 완전하게 모아둔 어플은 없었다는 것이다. 하나가 있으면 다른 것이 없곤 해서 늘 아쉬웠다.  
이번 프로젝트를 시작할 때 평소에 가졌던 작은 불만인 이것이 떠올라서 가볍게 기획안을 냈고 관심있는 사람들이 모여 습관을 만드는 어플리케이션을 만들게 되었다.  

### 1-2. 주요 기능

1. 회원가입 & 로그인 & 로그아웃 (+암호화)
2. 습관 만들기
3. 달력에 전체 습관에 대한 성공률 기록 (클릭해서 이전 날짜 보기 기능x)
4. 달력에 각 습관별 성공률 기록 (클릭해서 이전 날짜 보기 기능x)
5. 습관 추가 & 수정 & 삭제
6. 습관에 단위별로 기록할 수 있게 하기 (check, count, minute)
7. 완료했을 경우 표시하기
8. 특정 요일만 일정에 넣도록 하는 기능
9. 연속으로 며칠동안 진행했는지, 총 몇 번 했는지 보여주기

### 1-3. Flow
프로젝트를 시작하기 전 미리 설계했던 Flow이다.  
![ZeroTo66_Flow](https://user-images.githubusercontent.com/11348329/83354495-0c980c80-a394-11ea-8220-6851878e7ed8.jpg)

### 1-4. Schema
프로젝트를 시작하기 전 미리 설계했던 Schema이다.  
![ZeroTo66_Schema](https://user-images.githubusercontent.com/11348329/83354605-b8415c80-a394-11ea-84c5-3e6a39ee06ca.png)

### 1-5. 기술 Stack
프로젝트 때 사용했던 기술 스택은 아래와 같다.  
Front-End : React, HTML, CSS
Back-End : Mysql, Express, Sequelize, JWT
ETC : EC2, S3, RDS

### 1-6. React Component
프로젝트를 시작하기 전 미리 설계했던 React Component이다.  
![ZeroTo66_React_Component](https://user-images.githubusercontent.com/11348329/83354513-2f2a2580-a394-11ea-8dcd-d1ea96414d33.jpg)

## 2. 프로젝트 진행

### 2-1. Tasks
총 3개의 스프린트로 8일동안 진행했던 task이다.  
![ZeroTo66_Sprint1](https://user-images.githubusercontent.com/11348329/83355220-048e9b80-a399-11ea-8e4b-6d488f6f6fab.jpg)
![ZeroTo66_Sprint2](https://user-images.githubusercontent.com/11348329/83355218-03f60500-a399-11ea-954a-c93e75bc15cf.jpg)
![ZeroTo66_Sprint3-1](https://user-images.githubusercontent.com/11348329/83355217-02c4d800-a399-11ea-8e2a-cfe88b404bf8.jpg)
![ZeroTo66_Sprint3-2](https://user-images.githubusercontent.com/11348329/83355216-0193ab00-a399-11ea-96ab-cbbb0b2f029a.jpg)

### 2-2. API 문서

프로젝트를 진행하며 작성했던 API 문서이다.  
![ServerAPI_1](https://user-images.githubusercontent.com/11348329/83355330-d78eb880-a399-11ea-8577-35f110f3c207.png)
![ServerAPI_2](https://user-images.githubusercontent.com/11348329/83355329-d6f62200-a399-11ea-9662-5d69d60aa979.png)
![ServerAPI_3](https://user-images.githubusercontent.com/11348329/83355327-d65d8b80-a399-11ea-9927-6022e6b682fb.png)
![ServerAPI_4](https://user-images.githubusercontent.com/11348329/83355325-d52c5e80-a399-11ea-8935-02a6516c0c5c.png)

### 2-3. references

프로젝트를 진행하며 참고했던 자료들이다.  
UI 참고 : https://www.habitify.me/  
sequelize associate : https://victorydntmd.tistory.com/32  
sequelize 한글 문서 : https://velog.io/@cadenzah/sequelize-document-1  
HTTP 응답코드 메소드 정리 GET, POST, PUT, PATCH, DELETE, TRACE, OPTIONS : https://javaplant.tistory.com/18  
크롬에서 비밀번호 유출 메시지 뜨는 이유 : https://m.zdnet.co.kr/news_view.asp?article_id=20190206092407#_enliple  
dynamic origin of cors : https://expressjs.com/en/resources/middleware/cors.html  
로그아웃할 경우 token 처리 : https://stackoverflow.com/questions/37959945/how-to-destroy-jwt-tokens-on-logout  
JWT 이해하기 : https://medium.com/dev-bits/a-guide-for-adding-jwt-token-based-authentication-to-your-single-page-nodejs-applications-c403f7cf04f4  
Draw AWS diagrams : https://app.cloudcraft.co/  

## 3. 완성

### 3-1. 기능별 시연 gif
#### 회원가입 & 로그인 & 로그아웃
![signup login logout](https://user-images.githubusercontent.com/11348329/83355784-859b6200-a39c-11ea-9e17-a0ec645be6fe.gif)
#### 습관 만들기
![makeHabits](https://user-images.githubusercontent.com/11348329/83355782-83390800-a39c-11ea-8cf2-97fa1080612a.gif)
#### 달력에 전체 습관에 대한 기록
![totalCalendar](https://user-images.githubusercontent.com/11348329/83355785-86cc8f00-a39c-11ea-9584-52ac3315f251.gif)
#### 각 습관 별 정보와 완료할 때
![detailOfHabit](https://user-images.githubusercontent.com/11348329/83355780-80d6ae00-a39c-11ea-997e-269209f3d88b.gif)
#### 습관 수정 및 삭제
![modify delete](https://user-images.githubusercontent.com/11348329/83355783-846a3500-a39c-11ea-9e08-31abef0d9a0e.gif)

### 3-2. repositories
server : https://github.com/aiody/ZeroTo66-server.git  
client : https://github.com/aiody/ZeroTo66-client.git  

## 4. 후기
처음에 기획 단계에서 flow, schema, task를 미리 설정해두는 것이 프로젝트를 진행하는 것에 있어서 아주 강력한 무기가 된다는 것을 체험했다. 맨 땅에서 하나씩 쌓아 올라가는 경험 덕분에 무엇이든 만들 수 있을 것 같은 자신감도 생겼다. 클라이언트 쪽 코드가 많이 아쉽다. 덕분에 코드 리뷰를 할 때 어떤 관점에서 보고 피드백을 주어야 하는지 감이 잡힌다. 다음에는 프론트와 백엔드 양 쪽 다 잘 챙기면서 진행해야지.  

