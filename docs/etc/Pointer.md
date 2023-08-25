---
layout: default
title: (C/C++) 포인터
nav_order: 1
parent: ETC
---



## 📑 Pointer와 증감 연산자

```c
*p++; //p의 내용물을 구하고 포인터 이동
*++p; //p인터 이동 후 p의 내용물을 구함
(*p)++; //포인터의 내용물을 증가
++(*p); //포인터의 내용물을 증가
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

```c
int main(void) {

 int a[][2] = { {100, 200}, {300, 400} }, b[4];
 int *p = &a[0][0];

 b[0] = p[0]++; //(=(*p)++) 포인터의 값 대입 후, 포인터 값 변경
 printf("b[0] = %d\n", b[0]);      //100
 printf("pointer = %d\n", *p);     //101

 b[1] = *p++ +1;    //포인터의 값 대입 후, 포인터 이동    
 printf("b[1] = %d\n", b[1]);      //102
 printf("pointer = %d\n", *p);     //200

 b[2] = (*p)++; //포인터의 값 변경
 printf("b[2] = %d\n", b[2]);      //200
 printf("pointer = %d\n", *p);     //201

 p+=1;  //포인터 이동
 b[3] = ++*p;   //포인터의 값 변경
 printf("b[3] = %d\n", b[3]);      //301
 printf("pointer = %d\n", *p);     //301

 return 0;

}
```
