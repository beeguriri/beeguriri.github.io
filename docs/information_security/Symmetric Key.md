---
layout: default
title: 대칭키
nav_order: 6
parent: Information Security
---



## 📑 대칭키 암호 운영 모드

| 모드 | 유형   | 수식표현                                     | IV   | 오류전파 | 암호병행 | 복호병행 |
| ---- | ------ | -------------------------------------------- | ---- | -------- | -------- | -------- |
| ECB  | Block  | C_i = Ek(P_i)<br />P_i = Dk(C_i)             | X    | X        | O        | O        |
| EBC  | Block  | C_i = Ek(P_i+C_i-1)<br />P_i = Dk(C_i)+C_i-1 | O    | O        | X        | O        |
| CFB  | Stream | C_i = P_i+Ek(C_i-1)<br />P_i = C_i+Ek(C_i-1) | O    | O        | X        | O        |
| OFB  | Stream | C_i = P_i+Ek(S_i-1)<br />P_i = C_i+Ek(S_i-1) | O    | X        | X        | X        |
| CTR  | Stream | C_i = P_i+Ek(N_i)<br />P_i = C_i+Ek(N_i)     | O    | X        | O        | O        |

- EBC : 평문 블록을 `이전 암호문 블록`과 XOR 연산
- CFB : 이전 암호문이 다음 암호문의 입력이 됨
