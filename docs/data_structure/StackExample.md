---
layout: default
title: 스택 활용
nav_order: 10
parent: Data Structure
---



## 📑 스택 활용

### ⭐ 중위 표기를 스택을 이용하여 후위 표기로 바꾸기

- 숫자가 나오면 그대로 출력한다
- '(' 가 나오면 push (우선순위 가장 낮음)
- '*', '/' 가 나오면 push (우선순위 가장 높음)
- '+', '-'가 나오면
  - 열림 괄호 직전까지 pop 해서 연산자 출력
  - 열림 괄호 없으면 스택의 끝까지 pop 해서 연산자 출력
  - 연산자 push
- ')' 가 나오면
  - 열림 괄호까지 pop, 연산자는 출력

![](https://github.com/beeguriri/beeguriri.github.io/blob/main/docs/img/stack1.jpeg?raw=true)

### ⭐ 중위 표기 된 식을 스택을 이용하여 계산하기 

- 스택 2개 필요
- 처리 요소 우선순위 > 스택 top의 우선순위 => 연산자 push
- 처리 요소 우선순위 <= 스택 top의 우선순위 => 연산



### ⭐ 후위 표기 된 식을 스택을 이용하여 계산하기 

- 스택 1개 필요
- 처리할 요소가 연산자이면 스택에서 pop 2회 후 연산하고 push
- 연산자 우선순위 필요 없음, 괄호 필요 없음
