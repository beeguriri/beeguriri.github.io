---
layout: default
title: IP
nav_order: 3
parent: Network
---



## 📑 IPv4

- 헤더 크기 : 20 ~ 60 바이트
- 주소 길이 : 32bit (8bit * 4개, 10진수)
- 주소 체계는 클래스 개념을 사용(A, B, C) - 비순차적
- 전송 방식 : 유니캐스트, 브로드캐스트, 멀티캐스트



### ⭐ 서브네팅

- 호스트 번호 부분을 서브넷 번호와 호스트 번호로 세분화
- 외부 라우터가 내부 네트워크 조직을 모르게 하고,
- 라우팅 테이블의 크기를 줄이는 효과



## 📑 IPv6

- 헤더 크기 : 40 바이트 `고정`
- 주소 길이 : 128bit (16bit * 8개, 16진수)
- 주소 체계는 네트워크 규모, 단말기 수에 따른 순차적 할당
- IPv4의 주소 부족 문제 해결 (NAT와 같은 주소 변환 기술 불필요)
- 전송 방식 : 유니캐스트, 멀티캐스트, 애니캐스트
- 헤더 길이를 고정으로 변경
  - 패킷 단편화 관련 필드 삭제, 체크섬 필드 삭제
- 트래픽을 효과적으로 분류할 수 있는 기능 제공
  - Flow Label
- 보안기능 향상
  - 프로토콜 내 보안관련 기능 탑재할 수 있도록 설계
  - 확장헤더 통하여 종단간 암호화 제공
- 주소 자동 설정
  - MAC주소 + 라우터가 제공하는 네트워크 프리픽스에 결합하여 IP주소 자동 생성



## 📑 IPv4 vs IPv6

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/header.jpg?raw=true)

| IPv4                    | IPv6               |                                 |
| ----------------------- | ------------------ | ------------------------------- |
| version(4)              | version(4)         | 유지                            |
| header length(4)        | -                  | 삭제 (고정)                     |
| type of service(8)      | traffic class (8)  | 이름 변경 / 우선순위, 혼잡 알림 |
| -                       | flow label (20)    | 신규 / `연결 지향`              |
| total length(16)        | payload length(16) | 이름 변경                       |
| fragment identifier(16) | -                  | 삭제                            |
| fragment  flag(3)       | -                  | 삭제                            |
| fragment offset(13)     | -                  | 삭제                            |
| time to live(8)         | hop limit(8)       | 이름 변경                       |
| protocol(8)             | next header(8)     | 이름 변경                       |
| header checksum(16)     | -                  | 삭제 (데이터 신뢰성 보장)       |
| option                  | -                  | 삭제 (payload에 포함)           |



## 📑 IPv4 -> IPv6 변환

- 이중 스택 (동시 지원)
- 터널링
  - IPv6 사용하는 두 호스트 통신 중 IPv4 지역 지나는 경우
  - IPv4 패킷으로 캡슐화 -> IPv4 지역 통과 후 IPv6로 역캡슐화
- 헤더 변환
  - 수신자가 IPv4 사용 할 경우, 헤더 변환



## 📑 전송 방식

- 유니캐스트
  - 1:1
- 브로드캐스트
  - 한 명의 송신자가 같은 서브 네트워크 상 `모든 수신자`에게 일방적으로 데이터 전송
- 멀티캐스트
  - 한 명 이상의 송신자가 `특정한 다중 수신자`에게 데이터 전송
- 애니캐스트
  - 하나의 호스트에서, 같은 접두어 가진 멤버 중 하나의 호스트로 패킷 전송
  - 물리적으로 같은 네트워크는 같은 접두어를 가짐



## 📑 인터넷 계층 프로토콜

### ⭐ ICMP

- 송신측의 상황과 목적지 노드의 상황을 진단하는 프로토콜
- ICMP 메시지
  - ICMP Echo Request/Reply : 송신측 패킷이 목적지나 라우터에 도착했는지 확인
  - ICMP Destination Unreachable
  - ICMP Redirect : 해당 노드에 대한 최적화된 경로 다시 지정
  - CIMP Time Exceeded
  - ICMP Source Quench : 혼잡 제어



### ⭐ ARP / RARP

- 다음 네트워크 인터페이스의 MAC 주소 알아내는데 사용
- 브로드캐스트를 통해 특정 IP 주소 사용하는 호스트가 응답 하도록 요구하는 방식