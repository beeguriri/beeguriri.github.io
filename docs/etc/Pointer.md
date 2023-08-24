---
layout: default
title: 2진수
nav_order: 1
parent: ETC
---



## 📑 Pointer와 증감 연산자

```c
*p++; //p의 내용물을 구하고 p를 증가
*++p; //p를 증가시키고 p의 내용물을 구함
(*p)++; //p의 내용물을 증가
++(*p); //p의 내용물을 증가
```

```c
#include <stdio.h>
void main() {
    
    int a [] = {10, 20, 30, 40};
    int *p = a+1, y1, y2;
    *p++;			//pointer 이동, 30 가르키고 있음
    y1 = ++*p;		//30 -> 31로 증가
    *++p;			//pointer 이동, 40 가르킴
    y2 = (*p)++;	//p번지의 값을 구하고(y2=40), p번지의 값 40 -> 41로 증가
    printf("%d %d %d", y1, y2, a[3]); //31, 40, 41
}
```

