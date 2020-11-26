---
layout: post
title: "그래프(Graph)"
author: peter
categories: [DataStructure]
image: assets/images/5.jpg
tags:
sitemap:
changefreq: daily
priority: 1.0
---

---

{:toc}

### 그래프(graph)

- 트리가 1:n 구조의 자료구조 였다면 그래프는 n:n 구조의 자료구조이다.
- 그래프의 G는 (V, E)로 표시하는데, 이는 객체를 나타내는 **정점(vertex)**과 객체를 연결하는 **간선(edge)**으로 구성되어 있다.

- 정점(vertex): -- 노드라고도 불림

  - 여러 가지 특성을 가질 수 있는 객체를 의미
  - V(G): 그래프 G의 정점들의 집합<br><br>

- 간선(edge): -- 링크 - 정점들 간의 관계 의미 - E(G): 그래프 G의 간선들의 집합
  <img align="right" width="250" height="250" src= "https://user-images.githubusercontent.com/52132160/88883052-44c1ab80-d26e-11ea-9760-43423be7f747.png">

<br>
<br>
<br>
<br>

##### 그래프의 종류

1. 무방향 그래프(undirected graph)
   - 두 정점을 연결하는 간선에 방향이 없는 그래프
   - 정점 Vi와 Vj를 연결하는 간선을 (Vi, Vj)라고 나타낸다.
     **(Vi, Vj) = (Vj, Vi)**<br><br>

![image](https://user-images.githubusercontent.com/52132160/88881887-8f8df400-d26b-11ea-8153-bab577d4511f.png)
![image](https://user-images.githubusercontent.com/52132160/88881911-a0d70080-d26b-11ea-8272-5f87d13aebc8.png)

2. 방향 그래프(directed graph), digraph - 간선에 방향이 있는 그래프 - 정점 Vi에서 Vj를 연결하는 간선 즉, Vi -> Vj를 <Vi, Vj> 로 표현 - Vi를 tail, Vj를 head 라고 한다. - **<Vi, Vj>와 <Vj, Vi>**는 서로 다른 간선이다.
<p align="center">        
    <img width="400" height="200" src="https://user-images.githubusercontent.com/52132160/88882128-3a061700-d26c-11ea-94ff-c1ed69827eec.png">        
</p>

3. 가중치 그래프(weighted graph), 네트워크 - 간선에 비용(cost)이나 가중치(weight)가 할당된 그래프
   ![image](https://user-images.githubusercontent.com/52132160/88882569-3aeb7880-d26d-11ea-9589-49e5e5a66585.png)

- etc. 완전 그래프(complete graph), 부분 그래프(subgraph)등 이 존재한다.

---

---

#### 그래프의 구현

- 무방향, 방향 그래프 모두 **인접 행렬**과 **인접 리스트** 두 가지 방법을 통해 구현 가능하다.
- 나는 화살표로 고통받는 걸 좋아하기 때문에 인접 리스트로 구현해 보았다.

| ![image](https://user-images.githubusercontent.com/52132160/88883876-5015d680-d270-11ea-9b6c-286ab90e1ac7.png) |
| :------------------------------------------------------------------------------------------------------------: |
|                              <font size= "3">무방향 그래프 인접리스트 표현</font>                              |

| ![image](https://user-images.githubusercontent.com/52132160/88884514-bf3ffa80-d271-11ea-85b7-d21596143572.png) |
| :------------------------------------------------------------------------------------------------------------: |
|                               <font size= "3">방향 그래프 인접리스트 표현</font>                               |

#### 무방향 그래프.c

{% highlight cpp %}
#include<stdio.h>
#include<stdlib.h>
#define MAX 30

typedef int element;
typedef struct graphNode {
int vertex;
struct graphNode\* link;
}graphNode;

typedef struct graphType {
int n; // 정점 개수
graphNode\* adjList_H[MAX_VERTEX];
}graphType;

// 공백 그래프 생성
void createGraph(graphType\* g) {
int v;
g->n = 0;

    for (v = 0; v < MAX_VERTEX; v++) {
    	g->adjList_H[v] = NULL;
    }

void insertVertex(graphType\* g, int v) {
if (((g->n) + 1) > MAX_VERTEX) {
printf("\n 그래프 정점의 개수를 초과하였습니다!");
return;
}
g->n++;
}

void insertEdge(graphType* g, int u, int v) {
graphNode* node;
if (u >= g->n || v >= g->n) {
printf("\n 그래프에 없는 정점입니다!");
return;
}
node = (graphNode\*)malloc(sizeof(graphNode));
node->vertex = v;
node->link = g->adjList_H[u]; // NULL
g->adjList_H[u] = node;
}

int main() {
int i;
graphType _G9;
G9 = (graphType _)malloc(sizeof(graphType));
createGraph(G9);

    // 그래프 G9 구성
    for (i = 0; i < 7; i++)
    	insertVertex(G9, i);
    insertEdge(G9, 0, 2);
    insertEdge(G9, 0, 1);
    insertEdge(G9, 1, 4);
    insertEdge(G9, 1, 3);
    insertEdge(G9, 1, 0);
    insertEdge(G9, 2, 4);
    insertEdge(G9, 2, 0);
    insertEdge(G9, 3, 6);
    insertEdge(G9, 3, 1);
    insertEdge(G9, 4, 6);
    insertEdge(G9, 4, 2);
    insertEdge(G9, 4, 1);
    insertEdge(G9, 5, 6);
    insertEdge(G9, 6, 5);
    insertEdge(G9, 6, 4);
    insertEdge(G9, 6, 3);

    return 0;

}
{% endhighlight %}

#### 방향 그래프.c

{% highlight cpp %}
#include<stdio.h>
#include<stdlib.h>

#define MAX 20

typedef struct graphNode {
int vertex;
int indegree; // 진입차수
struct graphNode\* next;
}graphNode;

typedef struct graphType {
int n; // 정점
graphNode\* idxlist[MAX];
}graphType;

void InitGraph(graphType\* g) {
int v;
g->n = 0;

    for (v = 0; v < MAX; v++) {
    	g->idxlist[v] = NULL;
    }

}
void insertVertex(graphType\* g, int v) {
if (((g->n) + 1) > MAX) {
printf("\n 그래프 정점의 개수를 초과하였습니다!");
return;
}
g->n++;
}

void insertEdge(graphType* g, int u, int c, int v) {
graphNode* node;
if (u >= g->n || v >= g->n) {
printf("\n 그래프에 없는 정점입니다!");
return;
}
node = (graphNode\*)malloc(sizeof(graphNode));
node->vertex = v;
node->indegree = c;
node->next = g->idxlist[u]; // NULL
g->idxlist[u] = node;
}

int main() {
graphType* G9;
G9 = (graphType*)malloc(sizeof(graphType));
InitGraph(G9);

    for (int i = 0; i < 9; i++) {
    	insertVertex(G9, i);
    }

    insertEdge(G9, 0, 0, 2);
    insertEdge(G9, 0, 0, 1);

    insertEdge(G9, 1, 1, 4);
    insertEdge(G9, 1, 1, 3);


    insertEdge(G9, 2, 1, 5);
    insertEdge(G9, 2, 1, 4);


    insertEdge(G9, 3, 1, 6);


    insertEdge(G9, 4, 2, 7);


    insertEdge(G9, 5, 1, NULL);


    insertEdge(G9, 6, 1, 8);
    insertEdge(G9, 6, 1, 7);


    insertEdge(G9, 7, 2, NULL); // 없으면 vertex에 NULL로

    insertEdge(G9, 8, 1, NULL);

    return 0;

}
{% endhighlight %}

---
