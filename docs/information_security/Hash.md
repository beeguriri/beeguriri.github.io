---
layout: default
title: 단방향 암호
nav_order: 7
parent: Information Security
---



## 📑 해시 함수의 특성

### ⭐일방향성

- 프리 이미지 저항성
- h(m) = x에 대한 h(m') = x를 만족하는 `임의의 메시지 m'`를 찾는 것은 어려워야 한다



### ⭐ 약한 충돌 저항성

- 2차 프리이미지 저항성
- `m이 주어 졌을 때`, h(m) = h(m')을 찾는 것은 계산적으로 어려워야 한다



### ⭐ 강한 충돌 저항성

- h(m) = h(m')인 `서로 다른 임의의 m과 m'`를 찾는 것은 계산적으로 어려워야 한다
- 생일 공격에 취약