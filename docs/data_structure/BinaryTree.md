---
layout: default
title: 이진트리
nav_order: 1
parent: Data Structure
---



## 📑 이진트리

### ⭐ 이진트리의 성질

- n개의 노드를 가진 이진트리는 n-1개의 간선을 갖는다
- 이진트리 레벨 i에서의 최대 노드 수는 2^(i-1) (i>=1) 이다

- 깊이가 k인 이진트리의 경우 최소 k개의 노드를 가지며 최대 2^k -1개의 노드를 갖는다

- k개의 노드를 가지는 이진트리의 깊이는 최대 k, 최소 log2(k+1)이다

  

### ⭐ 이진트리의 종류

- 포화 이진트리 : 각 레벨에 노드가 꽉 차있음
- 완전 이진트리 : 높이가 k일때 레벨1부터 k-1까지는 노드가 모두 채워져있음
- 이진트리 : 자식 노드를 2개 가짐
- 배열기반 이진트리
  - 노드 i의 부모노드 인덱스 : i/2
  - 노드 i의 왼쪽 자식 노드 인덱스 : 2i
  - 노드 i의 왼쪽 자식 노드 인덱스 : 2i + 1



### ⭐ 이진트리의 순회

- 전위 순회 : root -> left -> right
- 중위 순회 : left -> root -> right
- 후위 순회 : left -> right -> root
- 재귀로 구현

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/tree1.jpeg?raw=true)

```c
//전위 순회
void PreorderTraverse(BTreeNode *bt) {

    if(bt==NULL)
        return;

    printf("%d ", bt->data);
    PreorderTraverse(bt->left);
    PreorderTraverse(bt->right);
}

//중위 순회
void InorderTraverse(BTreeNode *bt) {

    if(bt==NULL)
        return;

    InorderTraverse(bt->left);
    printf("%d ", bt->data);
    InorderTraverse(bt->right);
}

//후위순회
void PostorderTraverse(BTreeNode *bt) {

    if(bt==NULL)
        return;

    PostorderTraverse(bt->left);
    PostorderTraverse(bt->right);
    printf("%d ", bt->data);

}
```

