---
layout: post
title:  "OpenSourceSW Assignment <TEAM 3>"
date:   2023-12-19 09:03:36 +0530
categories: Opensource Kubenetes Jenkins Jekyll Giscus
---
<br><br>

## Team Members
권영훈, 김가을, 김나현, 정진서
<br><br>

---

<br><br>
## Jenkins Part (1p)
1. git event hooking (git push 되면 작동하도록)
2. 젠킨스로 블로그 노드와 연결, 블로그 노드에서 git pull 할 수 있도록 설정

## Jekyll Blog Part (2p)
1. jekyll 템플릿 아무거나 써서, 우리 organization에 레포 추가
2. 쿠버네티스로 블로그 서버 시작하는 작업 (jekyll serve 라던가) 추가
3. 댓글쪽 구현 완료되면 댓글 스크립트 jekyll에 복사 붙여넣기

## Giscus Comment Part (1p)
1. giscus self-hosted 하는 법 그대로 따라하기
2. giscus 쿠버네티스로 올리기
3. 구현 완료되면 블로그에 추가하는거 돕기
<br><br>

---

<br><br>
## 실습 구성
- 마스터 노드 1
- 워커 노드 1 - 젠킨스
- 워커 노드 2, 3  - 블로그
- 워커 노드 4 - self-hosted giscus

## 실습 과정
글을 쓴다 -> 깃헙에 올린다 -> 젠킨스가 받는다 
-> 블로그 노드 2개에 반영된다 -> 블로그에 반영된다 -> 블로그 접속 시 대충 로드밸런싱 되는거 설명 
-> 댓글도 작성해본다 -> 깃에 올라가는 거 확인한다 -> 블로그에도 적용되는 것 확인한다 
-> 끝~
