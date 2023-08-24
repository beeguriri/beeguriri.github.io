---
layout: default
title: AVL 트리
nav_order: 3
parent: Data Structure
---



## 📑 AVL트리

### ⭐ AVL트리의 성질

- 이진탐색 트리에 `Balance Factor`를 가짐
- 각 노트의 왼쪽 서브트리 높이와 오른쪽 서브트리의 높이의 차이가 1이하
- 삽입 삭제 연산 시 Balance Factor 확인해서 트리 재 구성

  - Balance Factor = 왼쪽 자식노드 높이 - 오른쪽 자식노드 높이

- 균형트리가 항상 보장되므로 탐색, 삽입, 삭제 모두 `O(longN)`

  

### ⭐ AVL트리의 회전

- LL : `(2,1)` N이 왼쪽 서브트리의 왼쪽에 삽입
- RR : `(-2,-1)` N이 오른쪽 서브트리의 오른쪽에 삽입
- LR : `(2,-1)` N이 왼쪽 서브트리의 오른쪽에 삽입
- RL : `(-2,1)` N이 오른쪽 서브트리의 왼쪽에 삽입

{: .note-title }

> 트리 재구성 시 기존 자식노드가 있으면
>
> 왼쪽 자식은 새로운 왼쪽 자식의 오른쪽에 삽입
>
> 오른쪽 자식은 새로운 오른쪽 자식의 왼쪽에 삽입



### ⭐ AVL트리의 삽입

- 삽입 위치 탐색 후 리프노드에 추가
- Balance Factor 확인하여 트리 재구성

{: .highlight }

> 7,  8, 0, 2, 1, 5, 3, 6, 4 순으로 데이터 삽입

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/avltree.PNG?raw=true)



### ⭐ AVL트리의 삭제

- 리프노드 없으면 : 삭제
- 리프노드 1개 있으면 : 자식노드를 삭제 노드로 위치 이동
- 리프노드 2개 있으면 : 삭제 노드보다 작은값 중 제일 큰 값 또는 큰 값 중 제일 작은 값을 삭제 노드위치로 이동
- Balance Factor 확인하여 트리 재구성
