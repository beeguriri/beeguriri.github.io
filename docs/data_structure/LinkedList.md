---
layout: default
title: LinkedList
nav_order: 9
parent: Data Structure
---



## 📑 LinkedList

```c
//LinkedList.h

typedef int LData;

typedef struct _node
{
    LData data;
    struct _node *next;
} Node;

typedef struct _linkedList
{
    Node *head;     //더미노드 가르킴
    Node *cur;      //참조 및 삭제
    Node *before;   //삭제

    int numOfData;
    int (*comp)(LData d1, LData d2);    //정렬 기준
} LinkedList;

typedef LinkedList List;
```

```c
//초기화
void ListInit(List *plist){
    //head == dummy node
    plist -> head = (Node*)malloc(sizeof(Node));
    plist -> head -> next = NULL;

    //정렬기준, data 개수 초기화
    plist -> comp = NULL;
    plist -> numOfData = 0;
}

//삽입
void SInsert(List *plist, LData data) {

    Node *newNode = (Node*)malloc(sizeof(Node));
    newNode -> data = data;

    Node *pred = plist -> head; //더미노드 가르킴

    //새 노드가 들어 갈 위치 확인
    while(pred->next != NULL && data > pred->next->data)
        pred = pred -> next;
    
    //노드 연결 바꿔줌
    newNode -> next = pred -> next;
    pred -> next = newNode;

    (plist->numOfData)++;

}

//탐색
//리스트의 첫번째 데이터 확인
int LFirst(List *plist, LData *pdata){

    if(plist -> head -> next == NULL)
        return FALSE;
    
    plist -> before = plist -> head;
    plist -> cur = plist -> head -> next;
    *pdata = plist -> cur -> data;

    return TRUE;
}

//리스트의 첫번째 이후 데이터 탐색
int LNext(List *plist, LData *pdata){

    if(plist -> cur -> next == NULL)
        return FALSE;
    
    plist -> before = plist -> cur;
    plist -> cur = plist -> cur -> next;
    *pdata = plist -> cur -> data;

    return TRUE;
}

//cur 위치의 데이터 삭제
LData LRemove(List *plist){
    
    Node *rpos = plist -> cur;
    LData rdata = rpos -> data;

    //연결을 바꿔주고
    //cur와 before가 가르키는 노드가 같아짐
    plist -> before -> next = plist -> cur -> next;
    plist -> cur = plist -> before;

    //삭제
    free(rpos);
    (plist -> numOfData)--;
    
    return rdata;
}
```



## 📑 Doubly Linked List

```c
typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
    struct _node *prev;
} Node;

typedef struct _dbDLinkedList{
    Node *head;
    Node *tail;
    Node *cur;

    int numOfData;
} DBDLinkedList;

typedef DBDLinkedList List;
```

```c
void ListInit(List *plist) {
    
    //head, tail에 더미노드 지정
    plist -> head = (Node*)malloc(sizeof(Node));
    plist -> tail = (Node*)malloc(sizeof(Node));

    //최초 리스트 선언 시
    //head는 tail 가르키고, tail은 head 가르킴
    plist -> head -> prev = NULL;
    plist -> head -> next = plist -> tail;

    plist -> tail -> prev = plist -> head;
    plist -> tail -> next = NULL;

    plist -> numOfData = 0;
}

//새 노드 꼬리에 추가하기
void InsertTail(List *plist, Data data) {

    Node *newNode = (Node*)malloc(sizeof(Node));
    newNode -> data = data;

    //tail의 앞에 newNode 추가
    newNode -> next = plist -> tail;
    newNode -> prev = plist -> tail -> prev;
    plist -> tail -> prev -> next = newNode;
    plist -> tail -> prev = newNode;

    (plist -> numOfData)++;

}

//탐색
int LFirst(List *plist, Data *pdata) {

    //head가 tail 가르키고, tail이 head 가르키면 리스트 비었음
    if(plist -> head -> next == plist -> tail)
        return FALSE;

    plist -> cur = plist -> head -> next;
    *pdata = plist -> cur -> data;

    return TRUE;
}

int LNext(List *plist, Data *pdata) {
    
    if(plist -> cur -> next == plist -> tail)
        return FALSE;

    plist -> cur = plist -> cur -> next;
    *pdata = plist -> cur -> data;

    return TRUE;
}

Data LRemove(List *plist) {

    Node *rpos = plist -> cur;
    Data rdata = rpos -> data;

    //연결 바꿔주고
    plist -> cur -> prev -> next = plist -> cur -> next;
    plist -> cur -> next -> prev = plist -> cur -> prev;

    //현재위치 조정
    plist -> cur = plist -> cur -> prev;

    free(rpos);
    (plist -> numOfData)--;

    return rdata;
}
```







