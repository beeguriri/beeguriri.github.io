---
layout: default
title: 이진탐색트리
nav_order: 2
parent: Data Structure
---



## 📑 이진 탐색 트리

- 정렬 되지 않은 데이터도 탐색할 수 있음
- 이진탐색트리의 노드에 저장된 키는 유일함
- 루트 노드의 키가 왼쪽 서브 트리를 구성하는 어떠한 노드의 키보다 크다
- 루트 노드의 키가 오른쪽 서브 트리를 구성하는 어떠한 노드의 키보다 작다
- 키 입력 순서에 따라 다른 모양을 가짐
- 이진탐색트리로 구성하고 `중위순회 하면 항상 오름차순`으로 정렬 된 결과를 얻음

### ⭐ 삽입

- 삽입 위치를 탐색 후 리프노드에 키 추가

### ⭐ 삭제

- 리프노드가 없을 때 : 단순 삭제
- 리프노드가 1개 있을 때 : 자식 노드를 삭제 노드 위치로 이동
- 리프노드가 2개 있을 때 : 
  - 삭제노드 보다 작은 값 중 제일 큰 값 또는
  - 삭제노드 보다 큰 값 중 제일 작은 값을 삭제 노드 위치로 이동
