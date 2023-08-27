---
layout: default
title: 허프만트리
nav_order: 4
parent: Data Structure
---



## 📑 허프만 비트리

### ⭐ 허프만 코딩

- 텍스트 압축을 위해 사용하는 방법
- 자주 출현하는 문자는 적은 비트의 코드로 변환
- 출현 빈도가 낮은 문자는 많은 비트의 코드로 변환하여
- 전체 데이터를 표현하는데 필요한 비트 수를 줄이는 방식
  



### ⭐ 허프만 트리

- 가중치 내림차순 정렬 한 후 가중치 더해가며 트리 만들기
- 가중치 더한 후 계산 한 가중치에 대해 다시 내림차순 정렬
- 외부노드에서 루트노드까지의 거리와 외부노드의 가중치 곱의 총 합 sum(qi*di)

{: .highlight }

> q1=2, q2=3, q3=5, q4=8, q5=7, q6=10인 허프만 트리

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/huffman.PNG?raw=true)
