---
layout: default
title: (참고) 뷰
nav_order: 10
parent: DataBase
---



## 📑 VIEW

### ⭐ 생성, 수정, 삭제

- 뷰는 논리적인  테이블이므로 독자적인 인덱스를 가질 수 없다
- 뷰의 정의만 시스템 카탈로그에 저장하였다가 필요시 실행시간에 테이블을 구축한다
- 데이터에 대한 보안을 제공한다
- 뷰는 또 다른 뷰의 정의에 사용 될 수 있다.



### ⭐ 생성, 수정, 삭제

```mysql
CREATE VIEW MYVIEW
AS
	SELECT A
	FROM B
	LEFT JOIN C
	ON B.KEY = C.KEY;
	
CREATE VIEW MYVIEW_SUM
AS
	SELECT UID, SUM(SALARY)
	FROM B
	GROUP BY UID;
```

```mysql
ALTER VIEW MYVIEW
AS
    SELECT A
	FROM B
	LEFT JOIN C
	ON B.KEY = C.KEY;
```

```mysql
DROP VIEW MYVIEW;
```

```mysql
-- 뷰 정보 조회
DESCRIBE MYVIEW;

-- 뷰 소스코드 확인 (기존 테이블)
SHOW CREATE VIEW MYVIEW;
```





### ⭐ 뷰를 통해 기존 테이블에 데이터 입력

- 기존 테이블의 NOT NULL 열이 `뷰에 모두 포함` -> 데이터 입력 가능
- 기존 테이블의 NOT NULL 열이 뷰에 미포함 -> 수정 필요
  - NOT NULL 열의 DEFAULT값 설정
  - NOT NULL 조건 -> NULL 조건으로 변경

- WITH CHECK OPTION : 조건에 맞는 데이터만 입력 됨
- `기존 테이블의 열을 수정하여 만든 뷰`는 기존 테이블의 데이터 수정, 삭제 불가
  - 집계함수, UNION, GROUP BY, DISTINCT, JOIN


