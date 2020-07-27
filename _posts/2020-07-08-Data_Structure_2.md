---
layout: post
title:  "스택과 큐"
author: Peter
categories: [ DataStructure ]
image: assets/images/14.jpg
tags: 
sitemap:
changefreq: daily
priority: 1.0
---

---
### 스택의 개념 
- 한 쪽이 막힌 바구니의 형태다.

- 넣은 데이터는 아래쪽에 쌓인다.

- 후입선출(LIFO:Last in first out): 가장 최근에 들어온 데이터가 가장 먼저 나간다.

---

### 스택과 큐
- 배열/리스트 vs 스택/큐
    - 공통점: <u>선형 구조</u> 이다.
    - 차이점: 삽입과 삭제의 위치 고정 여부
        - 배열/리스트: 임의의 위치에서 삽입/삭제
        - 스택: 맨 위(top)
        - 큐: 
            - 삽입: 맨 앞(front)
            - 삭제: 맨 뒤(rear) 

---
### 스택의 구현
- 배열을 이용한 구현 
{% highlight cpp %}
typedef struct Stack{
    int top;
    int arr[STACK];
}ArrayStack; 
{% endhighlight %}

- 연결 자료구조(연결 리스트)를 이용한 구현
{% highlight cpp %}
typedef struct StackNode{
    int data; // 넣어줄 데이터 
    struct Node* next; // 연결을 위한 자기참조 포인터 
}Node; 

typedef struct LinkedStack{
    Node* top; // top 표시
}Node; 
{% endhighlight %}

---
---
#### 배열 스택의 구현.cpp
{% highlight cpp %}
#define	MAX_STACK_SIZE 50
#define True 1
#define False 0

typedef  int  Bool;
typedef  int  Element;

typedef struct { 
   Element  stackArr[MAX_STACK_SIZE];
   int	top;
} Stack;

// 스택 생성
Stack *Create(void) {
   Stack *tempstack;
	
   tempstack = malloc(sizeof(Stack));
   tempstack->top = -1; // 맨 아래에 있음
   return tempstack;
}

// 스택이 비었는 지 확인
Bool  isEmpty(Stack *pstack)
{
   if (pstack->top == -1)
      return True;
   else return False;
}

// 스택이 포화 상태인가
Bool isFull(Stack *pstack)
{
   if (pstack->top == MAX_STACK_SIZE-1) // top은 -1부터 시작하기 때문에
      return True;
   else
      return False;
}

// 스택에 삽입 
void  Push(Stack *pstack, Element Data)
{
    if(isFull(pstack)){
    printf("Stack Overflow. \n");
    exit(-1);
    }
    pstack->top += 1;
    pstack->stackArr[pstack->top] = Data;
}

//스택에서 삭제
Element  Pop(Stack *pstack)
{
    if(isEmpty(pstack)){
    printf("Stack underflow. \n");
    exit(-1);
    }
   return pstack->stackArr[pstack->top--];
}

// 마지막에 무엇이 있는지 확인
Element peek(){
    if(isEmpty(pstack)){
        printf("ERROR");
        exit(-1);
    }
    return pstack->stackArr[pstack->top];
}

int main( ) {
   Stack *pstack;
   int a;
	
   pstack = Create();
   Push(pstack, 1);
   a = Pop(pstack);
   printf("%d\n", a);
  return 0;
}
{% endhighlight %}
- 배열로 구현한 스택의 장단점
    - 장점: 쉽게 구현 가능하다
    - 단점: 
        - 스택의 크기 변경이 어렵다
        - 순차 자료구조의 단점을 가진다. 

---
#### 연결리스트 스택의 구현.cpp
{% highlight cpp %}
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

typedef int element;

typedef struct stackNode{
    element data;
    struct stackNodeType* link; 
}stackNode;

typedef struct LinkedStackType{ 
    stackNode* top;
}LinkedStack;

type LinkedStack Stack;

void StackInit(Stack* pstack){
    pstack->top = NULL;
}

element isEmpty(Stack* pstack){
    if(pstack->top == NULL)
        return 1;
    return 0;
}

void push(Stack* pstack, element item){
    stackNode* newNode = (stackNode*)malloc(sizeof(stackNode));
    newNode->data = data;
    newNode->link = pstack->top;
    pstack->top = newNode;
}

element pop(Stack* pstack){
    element rdata;
    stackNode* rnode;
    if(isEmpty(pstack)){
        printf("\n\n Stack is empty!\n");
        exit(-1);
    }
    else{
        rdata = pstack->top->data;
        rnode = pstack->top;
        pstack->top = pstack->top->link;
        free(rnode);
        return rdata;
    }
}

elememt peek(Stack* pstack){
    if(isEmpty(pstack)){
        printf("\n\n Stack is empty! \n");
        exit(-1);
    }
    return pstack->top->data;
}
{% endhighlight %}

