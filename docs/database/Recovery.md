---
layout: default
title: 회복기법
nav_order: 2
parent: DataBase
---



## 📑 트랜잭션 회복기법

### ⭐ Undo, Redo

- Redo : 오류가 발생한 트랜잭션 재실행하여 복구, 로그에 `Start` `Commit` 이 있음
- Undo : 오류와 관련된 모든 변경 취소, 로그에 `Start` 만 있음

### ⭐ 로그 기반 회복 기법

- 지연 갱신 회복 기법
  - 커밋이 발생하기 전까지는 DB에 기록하지 않음
  - 변경 내용은 로그에 기록
  - 중간에 장애가 발생하더라도 기록되지 않았으므로 Undo 필요 없음
  - Commit이 완료 된 것은 Redo

- 즉시 갱신 회복 기법
  - 트랜잭션 수행 도중에도 변경내용을 즉시 DB에 기록
  - Commit 완료 된 것은 Redo 
  - Commit 완료 되지 않은 것은 Undo


### ⭐ 검사점 회복 기법

- 검사점 이전에 처리 된 트랜잭션은 회복에서 제외
- 검사점 이후에 처리된 트랜잭션은 회복 작업 수행
  - 검사점 이후, 장애 발생 이전에 commit이 완료 된 경우 Undo 실행
  - 장애 발생 시점까지 commit이 되지 못한 경우 Redo 실행
- 수행 알고리즘
  - Undo, Redo List 생성 후 모든 트랜잭션 Undo list에 삽입
  - 로그 순차 검색해서 Start 상태이면 Undo, 
  - Commit 상태이면 Undo list에서 제거 후 Redo list에 삽입
  - Undo List 역순으로 연산 수행 후 Redo list 순서대로 연산 실행

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/recovery1.png?raw=true)

{: .highlight}

> - Redo : T2, T4
> - Undo : T3, T5
> - T1은 check point 이전에 commit이 완료되었으므로 회복에서 제외



![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/recovery2.png?raw=true)

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/recovery3.PNG?raw=true)
