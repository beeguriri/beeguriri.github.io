---
layout: default
title: 네트워크 보호
nav_order: 4
parent: Information Security
---



## 📑 침입 차단 시스템 : 방화벽

- 외부 네트워크와 내부 네트워크 사이에 일종의 보호막 제공
- 접근 제어 목록(ACL)을 통해 네트워크에 전송되는 트래픽에 대한 보안 정책 설정



### ⭐ 주요 기능

- 접근 통제 : 패킷 필터링 (외부 -> 내부 접속 통제)
- 사용자 인증
- 감사 및 로그 기능 : 모든 트래픽에 대한 접속 정보 및 네트워크 사용에 따른 유용한 통계정보 기록
- 프록시 기능 : 클라이언트의 서비스 요청을 실제 수행하는 서버
- 주소 변환 기능(NAT) : 호스트의 IP 주소를 전송 단계에서 변경하여 전달



### ⭐ 차단 방법에 따른 분류

- 패킷 필터링

  - `패킷의 헤더`에 저장 된 정보를 이용
  - TCP 연결 상태에 대한 검사 불가

- 상태(stateful) 검사

  - `패킷`을 대상으로 검사
  - 전체 계층에 대한 상태를 조사할 수 있음
  - TCP 연결에 관한 정보를 기록
  - TCP 순서 번호를 추적해 세션하이재킹 같은 공격 막음

- 응용 필터링

  - `세션`에 보함된 정보 유해성 검사
  - 세션을 중간에서 분리하여 중계
    - 기존 세션을 종료하고 새로운 세션 형성
  - 프락시 서비스를 사용 (응용 서비스별로 제공 가능)
  - 외부의 네트워크와 직접적인 연결을 피할 수 있고, 
  - 내부 IP 주소를 노출 시키지 않음으로써 내부 네트워크 정보 보호

  

### ⭐ 구성 방법에 따른 분류

- 듀얼 홈드 게이트웨이
- 스크린 호스트 게이트웨이 : 베스천 호스트 + 스크린 라우터
- 스크린 서브넷 게이트웨이 : 스크린 네트워크 구성



## 📑 침입 탐지 시스템

- 악의적인 공격을 발견하고 보고하는 보안 솔루션
- 전달 되는 메시지 내용을 분석하여 정상/공격 판단
- 공격을 차단하는 것 X, 탐지하고 알려줌 O
- 예방 시설 강화에 목적



### ⭐ 기능

- 데이터 수집
- 데이터 필터링 및 축약
- 분석 및 침입 탐지
- 보고 및 대응



### ⭐ 종류

- 오용 탐지
  - False Negative (실제 침입이지만 침입이 아니라고 탐지) 높음
  - 시그니처 분석 : `알려진 공격`이나 시스템 오용과 관련된 것을 규정 한 패턴
- 이상 탐지
  - False Positive (실제 침입이 아니지만 침입이라고 탐지) 높음
  - 정상적 행위 패턴으로부터 그 `편차`를 찾아냄



## 📑 VPN

- 공중망 서비스에 `터널링 기법`을 이용하여 전용선처럼 사용
- 응용 프로그램 하단 계층에서 작동하므로 응용 프로그램을 수정할 필요 없음



### ⭐ 터널링 기술

- PPTP
- IPSec : 기밀성, 데이터 인증, 연결 무결성
- SOCKSv5 : 세션 계층에서의 데이터 흐름 통제
- TLS VPN : IPSec 적용할 수 없는 구간에 사설 네트워크에 접속할 수 있는 방법 제공



### ⭐ 암호화 기술

- 데이터 기밀성을 위해 암호화 기술 사용



## 📑 IPSec

- 인증(MAC), 기밀성(ESP), 키관리(IKE)



### ⭐ 프로토콜

- AH (인증 헤더 프로토콜) : 인증, 무결성
- ESP : 인증, 무결성, `기밀성`



### ⭐ 운용 모드

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/ipsec.png?raw=true)

- 전송모드 : `페이로드만` 암호화, 호스트-호스트 데이터 보호 필요할 때 사용
- 터널모드 : `IP패킷 전체` 암호화