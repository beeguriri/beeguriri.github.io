---
layout: default
title: 운영체제 보안
nav_order: 6
parent: Information Security
---



## 📑 백업 유틸리티

- ntbackup

|           | Archive bit | 특징                                                         |
| --------- | ----------- | ------------------------------------------------------------ |
| 일반 백업 | 해제        | 선택된 파일 모두 백업                                        |
| 복사 백업 | 해제X       | 선택된 파일 모두 백업<br />특정 파일을 백업하는데 유용       |
| 매일 백업 | 해제X       | 그날 생성된 파일과 변경된 파일만 백업<br />매일 생성되는 데이터 백업에 유용 |
| 차등 백업 | 해제X       | 선택된 파일 중 Archive bit가 있는 파일만 백업<br />차등 백업 된 파일들은 나중에 재 백업 |
| 증분 백업 | 해제        | 선택된 파일 중 Archive bit가 있는 파일만 백업<br />이전 백업 후 변경된 파일 만을 백업할 때 이용 |

