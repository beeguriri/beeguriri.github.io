---
layout: default
title: 실시간 스케줄링
nav_order: 4
parent: os
---



## 📑 실시간 스케줄링

- 모든 프로세스들이 정해진 마감시간 내에 완료

### ⭐ RM (Rate Monotic) 

- 정적 스케줄링
- 프로세스의 주기가 짧을수록 높은 우선순위

{: .highlight }

> 예제 1 : 마감 시간 지킴
>
> p1 : 주기 50, 수행 시간 20
>
> p2 : 주기 50, 수행 시간 35

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/rm1.jpeg?raw=true)

{: .highlight }

> 예제 2 : 마감 시간 못 지킴
>
> p1 : 주기 50, 수행 시간 25
>
> p2 : 주기 80, 수행 시간 35

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/rm2.jpeg?raw=true)

### ⭐ EDF(Earliest Deadline First)

- 동적 스케줄링
- 마감 시간이 빠를수록 우선순위 높아짐
- 프로세스 실행 가능하면 자신의 마감 시간을 시스템에 알려줘야 함
- 프로세스 마감 시간은 다음 주기 시작 전

{: .highlight }

> 예제 3
>
> p1 : 주기 50, 수행 시간 25
>
> p2 : 주기 80, 수행 시간 35

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/edf.png?raw=true)

- t0 : p1 마감 50, p2 마감 80 => p1 우선
- t50 : p1 마감 100, p2 마감 80 => p2 우선
- t80 : p1 마감 100, p2 마감 160 => p1 우선
- t100 : p1 마감 150, p2 마감 160 => p1 우선
