---
layout: default
title: (참고) Unix
nav_order: 10
parent: os
---



## 📑 지명 파이프

- 하나의 프로세스 정보를 다른 프로세스로 전송할 때 사용
- 병행성 메커니즘의 한 종류
- 한 번에 한 개의 프로세스만 파이프에 접근 가능
- 두 프로세스가 통신할 수 있는 원형 버퍼
- 한 프로세스가 쓰고 다른 프로세스가 읽는 선입선출(FIFO) 형태의 큐 구조
- 파이프에는 일정한 공간이 할당 되어 있음



### ⭐ 종류

- `지명 파이프` : `서로 관련이 없는 프로세스들`도 공유할 수 있음
- 무명 파이프 : 서로 관련이 있는 프로세스들만 공유할 수 있음