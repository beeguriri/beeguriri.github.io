---
layout: default
title: DataBase
nav_order: 3
has_children: true
permalink: /docs/database
---



## 📑 데이터베이스

### ⭐ 무결성 제약조건

- NOT NULL
- UNIQUE : null값은 unique 제약 적용되지 않음
- PRIMARY KEY : NOT NULL + UNIQUE
- CHECK : 범위나 조건을 지정하여 설정한 값만 허용
- FOREIGN KEY : 참조되는 테이블의 칼럼값이 존재하면 허용