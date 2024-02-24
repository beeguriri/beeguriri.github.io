---
layout: default
title: Network
nav_order: 4
has_children: true
permalink: /docs/network
---



## 📑 데이터 교환 방식에 따른 네트워크 분류

### ⭐ 회선 교환

- 노드와 노드 간 `물리적 전용 통신로`를 설정하여 데이터 교환
- 송신자의 모든 데이터는 동일한 경로로 전송
- 대용량, 고속, 연속 데이터 처리에 우수
- 전송 지연 발생하지 않음
- 속도 변화나 트래픽 처리에 동적으로 대처하기 어려움



### ⭐ 메시지 교환

- 노드와 노드 간의 `중계 노드`에서 수신한 데이터를 `일단 메모리에 저장` 후 노드를 선택하여 송신
- 데이터 실시간 전송 불가능
- 전송 중 에러 발생해도 사본 재전송 할 수 있음
- 같은 메시지를 여러 노드에 동시 전송 할 수 있음



### ⭐ 데이터그램 (패킷 교환)

- 비연결형 서비스
- 전송되는 패킷은 `패킷 별로 경로 최적화` 하여 전송 (경로 동적 설정)
- 송신 패킷과 수신 패킷 순서 다를 수 있음
- 패킷에 우선순위 부여 가능
- 전송 속도 및 흐름 제어 가능
- 에러 탐지 가능
- 경로에서의 각 교환기에서 `전송지연` 다소 발생
- 임의 연결 요청에 대해 고정 대역을 할당하지 않으므로 이론 상 호스트 무제한 수용



### ⭐ 가상회선 방식

- 연결형 서비스
- 전송 시작 시 두 지점 사이에 `논리적인 전송 경로` 설정
  - 데이터 전송 전에만 경로가 바뀌고, 전송중일때는 바뀌지 않음 (회선교환 + 패킷교환)

- 많은 양의 데이터 연속으로 보낼 수 있음
- 패킷이 보낸 순서대로 도착, 오류 제어 쉬움
- 노드에 장애가 발생하면 그 노드를 경유하는 모든 가상회선이 사용 불가능
- 노드에 부하가 크면 `전송 지연` 발생





## 📑 네트워크 토폴로지

### ⭐ 버스형

- 버스 양 끝에 `터미네이터`를 둠
- 버스의 어느 한 곳이 단절되면, 전체 네트워크 중단
- 한 컴퓨터에서 고장이 발생하면 파급효과 적음
- 하나의 버스를 공유하므로 큰 데이터 전송에는 부적합

### ⭐ 성형

- 허브는 여러 대의 컴퓨터를 `별모양`으로 서로 연결할 수 있음

### ⭐ 링형

- FDDI(Fiber Distributed Data Interface)
- 광케이블 LAN의 데이터 전송 표준

### ⭐ 트리형

- 허브는 네트워크를 `트리형`으로 연결할 수 있음

### ⭐ 메시형