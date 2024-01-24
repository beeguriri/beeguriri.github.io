---
layout: default
title: MySQL 중복 data 입력 검증
nav_order: 3
parent: DataBase
---



## 📑 MySQL 중복 데이터 입력 검증

### ⭐ INSERT IGNORE
- 중복 데이터 삽입 무시
- return 1 : 정상 입력
- return 0 : 중복 발생
```sql
INSERT IGNORE INTO TEST SET NAME = 'HELLO', CNT = 1; --정상입력
INSERT IGNORE INTO TEST SET NAME = 'SPRING', CNT = CNT+1; --정상입력
INSERT IGNORE INTO TEST SET NAME = 'HELLO', CNT = CNT+1; --NAME UNIQUE 위배, 데이터 입력 안됨
INSERT IGNORE INTO TEST SET NAME = 'SPRING2', CNT = CNT+1; --정상입력
INSERT IGNORE INTO TEST SET ID = 1, NAME = 'SPRING3', CNT = CNT+1; -- PRIMARY KEY 위배, 데이터 입력 안됨
INSERT IGNORE INTO TEST SET NAME = 'SPRING4', CNT = CNT+1; --정상입력
```
![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/dup_before.png?raw=true)

### ⭐ REPLACE INTO
- 중복 발생 시 기존 데이터 삭제 후 새로운 데이터 입력
- 단점 : AUTO_INCREMENT의 PRIMARY KEY 값이 변경 됨
```sql
REPLACE INTO TEST (NAME, CNT) VALUE ('SPRING', 11);
```
![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/dup_after.png?raw=true)

### ⭐ INSERT INTO ... ON DUPLICATE KEY UPDATE
- 중복 발생 시 업데이트 항목 지정
```sql
INSERT INTO TEST (NAME, CNT) VALUES ('SPRING', 3) 
	ON DUPLICATE KEY UPDATE cnt = cnt + 1;
```
![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/dup_duplicate.png?raw=true)