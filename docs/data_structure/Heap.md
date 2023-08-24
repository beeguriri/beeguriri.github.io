---
layout: default
title: 힙
nav_order: 5
parent: Data Structure
---



## 📑 힙

### ⭐ 힙의 성질

- 완전이진트리로 구성
- 최소힙 : 부모노드는 자식노드보다 크지 않다
- 최대힙 : 부모노드는 자식노드보다 작지 않다

- 자식 i의 부모노드 인덱스 : `i/2`
- 부모 i의 자식 왼쪽노드 인덱스 `i*2`, 오른쪽노드 인덱스 `i*2+1`
- 힙의 높이는 log\(n+1)이므로, 시간복잡도 `O(logn)`
- 완전이진트리이므로 `배열`을 이용해서 구현, index=1 부터 사용

```c
#include <stdio.h>
#define MAX_SIZE 100
 
typedef struct{
    int key;
}Element;    
 
typedef struct{
    Element heap[MAX_SIZE];     
    int size;
};
```



### ⭐ 힙의 삽입

- 새로운 요소는 힙의 마지막 노드에 위치
- `아래에서 위`로 올라가면서 부모 노드와 비교해서 우선순위에 따라 위치 교환

```c
//최대 힙에서의 삽입
void Insert(Element data, int *n){	//n : 힙의 현재 사이즈
    
    //제일 마지막에 데이터 추가 후 교환
    int idx = ++(*n);

    while(idx!=1 && data.key > heap[idx/2].key) {
        //data가 더 크면(우선순위 높으면) 계속 반복
        heap[idx] = heap[idx/2];
        idx /= 2;
    }

    heap[idx] = data;
}
```



### ⭐ 힙의 삭제

- 루트 노드부터 삭제 됨
- 제일 마지막 노드에 있는 데이터를 루트노드에 위치 시킨 후
- `위에서 아래로` 내려가면서 자식 노드와 비교 해 우선순위에 따라 위치 교환

```c
//최대 힙에서의 삭제
Element Delete(int *n) {

    //우선순위 높은순으로 꺼냄
    //루트노드 제거 후, 제일 마지막값을 루트노드에 배치하여
    //우선순위 비교
    Element delData = heap[1];
    Element temp = heap[(*n)--];

    int parent = 1;
    int child = 2;

    while(child <= *n) {

        //자식노드 왼쪽, 오른쪽 비교해서 더 큰쪽 선택
        if(child < *n && heap[child].key < heap[child+1].key)
            child++;
        
        //temp가 자식노드보다 크거나 같으면 반복문 종료
        if(temp.key >= heap[child].key)
            break;
        
        heap[parent] = heap[child];
        parent = child;
        child *= 2;
    }

    heap[parent] = temp;

    return delData;

}
```
