---
layout: post
title: "트리"
author: peter
categories: [DataStructure]
image: assets/images/7.jpg
tags:
sitemap:
changefreq: daily
priority: 1.0

use_math: true
---

---

### 트리(tree)

앞서 다뤘던 리스트, 스택, 큐 등은 **선형 자료구조**(1:1)이다.

이에 반해 **트리**는 계층적인 구조를 나타내는 **비선형 자료구조**이다.

정리하면 트리는

    - 원소들 간에 1:N 관계를 가지는 비선형 자료구조
    - 원소들 간에 계층 관계를 가지는 구조(부모-자식 구조)이다.

---

##### 트리 용어

    - 루트(root) 노드: 트리의 첫 번째 노드(2번 노드에 해당)
    - 단말(leap or terminal) 노드: 자식이 없는 노드(5, 11, 4번 노드가 해당)
    - 내부(internal) 노드: 적어도 하나의 자식을 가지는 노드(단말 노드가 아닌 노드)
    - 트리의 높이(height): 루트 노드에서 가장 먼 거리에 있는 자식 노드에 이르는 간선들의 수 + 1
    - 차수(degree): 한 노드가 가지는 자식 노드의 개수

![300px-Binary_tree svg](https://user-images.githubusercontent.com/52132160/88499076-d5df1b00-cfff-11ea-820d-f2930155a4a8.png)

---

#### 이진 트리(binary tree)

- 트리의 모든 노드의 차수를 2 이하로 제한하는 트리 형식

- 이진 트리의 모든 노드는 왼쪽 자식 노드와 오른쪽 자식 노드만을 가짐
  - 0 <= 노드의 차수 <= 2
- 노드의 개수가 n개 이면 간선의 개수는 n-1개이다.

- 높이가 h인 이진 트리의 경우
  - 최소 h개의 노드 ~ 최대 $$ 2^h - 1 $$ 개의 노드
- n개의 노드를 가지는 이진 트리의 높이
  - 최소 $$log2(n+1)$$ ~ 최대 n

---

##### 이진 트리의 분류

1. 포화 이진 트리(full binary tree): 단말 노드를 제외한 모든 노드가 2개의 자식 노드을 가짐
2. 완전 이진 트리(complete binary tree): **왼쪽**부터 순서대로 채워진 트리
3. 편향 이진 트리: 노드가 왼쪽 또는 오른쪽 한 방향으로만 서브 트리를 가진 트리
4. 기타 이진 트리

![이진트리2](https://user-images.githubusercontent.com/52132160/88501438-6c163f80-d006-11ea-9e0a-c14275219b52.PNG)

##### 연결리스트를 이용한 이진 트리 구현.c

{% highlight cpp %}
typedef struct Node {
char data;
struct Node* left;
struct Node* right;
}Node;
{% endhighlight %}

    - 자식 노드가 없으면 NULL 포인터로 설정
    - 데이터 필드, 왼쪽 링크 필드(왼쪽 노드 포인터), 오른쪽 링크 필드(오른쪽 노드 포인터)를 구성

![포인터 이진트리](https://user-images.githubusercontent.com/52132160/88502963-20b26000-d00b-11ea-8886-e95ab01c2190.PNG)
![포인터 이진트리2](https://user-images.githubusercontent.com/52132160/88503036-666f2880-d00b-11ea-83a6-6ca2bccb21bb.PNG)

#### 이진트리의 순회

순회란? 모든 노드를 빠트리거나 중복하지 않고 처리하는 연산
--> 다양한 순회 방법이 존재한다(전위, 중위, 후위, 레벨 순회)

---

![트리예시](https://user-images.githubusercontent.com/52132160/88504204-f1055700-d00e-11ea-81f7-747026d21659.PNG)

1. 전위 순회(preorder traverse): root(최우선)->left->right

   - 순회 순서: 1(root) -> 2(root) -> 4 -> 5 -> 3(root) -> 6 -> 7

2. 중위 순회(inorder traverse): left -> root -> right

   - 순서: 4 -> 2 -> 5 -> 1 -> 6 -> 3 -> 7

3. 후위 순회(postorder traverse): left -> right -> root

   - 순서: 4 -> 5 -> 2 -> 6 -> 7 -> 3 -> 1

4. 레벨 순회(level traverse): 각 노드를 레벨 순으로 검사 및 순회, **큐** 사용
   - 순서: 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7

---

##### 반복문을 이용한 트리 순회.c

{% highlight cpp %}
#include<stdio.h>
#include<stdlib.h>
#define MAX 15

int top = -1;
int front = 0;
int rear = 0;

typedef struct treeNode {
char data;
struct treeNode *left;
struct treeNode *right;
} treeNode;

treeNode* stack[MAX];
treeNode* queue[MAX]; // 레벨 순회를 위한 큐

treeNode* makeRootNode(char data, treeNode* leftNode, treeNode* rightNode) {
treeNode* root = (treeNode \*)malloc(sizeof(treeNode));
root->data = data;
root->left = leftNode;
root->right = rightNode;
return root;
}

void push(treeNode* node, int* top) {
if (\*top == MAX - 1) {
printf("Stack Overflow");
exit(-1);
}

    stack[++(*top)] = node;

}

treeNode* pop(int* top) {
if (*top == -1) {
exit(1);
}
return stack[(*top)--];
}

void insert(int front, int* rear, treeNode* Tnode) {
*rear = (*rear + 1) % MAX;
if (*rear == front) {
printf("Queue is Full");
exit(1);
}
queue[*rear] = Tnode;
}

treeNode* Delete(int* front, int rear) {
if (*front == rear) {
exit(1);
}
*front = (*front + 1) % MAX;
return queue[*front];
}

//전위
void preorder(treeNode* Tnode) {
treeNode* temp = Tnode;
push(temp, &top);
while (top != -1) {
temp = pop(&top);
printf("%c ", temp->data);
if (temp->right != NULL) {
push(temp->right, &top);
}
if (temp->left != NULL) {
push(temp->left, &top);
}
}
printf("\n");
}

//중위
void inorder(treeNode* Tnode) {
treeNode* temp= Tnode;
while (1) {
for (; temp; temp = temp->left) {
push(temp, &top);
}
if (top != -1) {
temp = pop(&top);
}
if (!temp) break;
printf("%c ", temp->data);
temp = temp->right;

    }
    printf("\n");

}

//후위
void postorder(treeNode* Tnode) {
treeNode* temp = Tnode;
treeNode\* check = NULL;
while (1) {
if (temp != NULL && temp != check) {
push(temp, &top);
do {
if (temp->right != NULL) push(temp->right, &top);
if (temp->left != NULL) push(temp->left, &top);
temp = temp->left;
} while (temp != NULL);
}
if (top != -1) {
temp = pop(&top);
if (temp->left != NULL && temp->right == NULL && temp->left != check) {
push(temp, &top);
temp = temp->left;
}
if (temp->right == NULL || temp->right == check) {
printf("%c ", temp->data);
check = temp;
}
}
else break;
}
printf("\n");
}

//레벨
void level(treeNode* Tnode) {
treeNode* temp = Tnode;

    if (!temp) return;
    insert(front, &rear, temp);
    while (1) {
    	temp = Delete(&front, rear);
    	if (temp) {
    		printf("%c ", temp->data);
    		if (temp->left) {
    			insert(front, &rear, temp->left);
    		}
    		if (temp->right) {
    			insert(front, &rear, temp->right);
    		}
    	}
    	else break;
    }
    printf("\n");

}

int main() {
treeNode* n13 = makeRootNode('!', NULL, NULL);
treeNode* n11 = makeRootNode('D', NULL, NULL);
treeNode* n10 = makeRootNode('L', NULL, NULL);
treeNode* n8 = makeRootNode('R', NULL, NULL);
treeNode* n7 = makeRootNode('O', NULL, NULL);
treeNode* n6 = makeRootNode('W', NULL, n13);
treeNode* n5 = makeRootNode('O', n10, n11);
treeNode* n4 = makeRootNode('L', n8, NULL);
treeNode* n3 = makeRootNode('L', n6, n7);
treeNode* n2 = makeRootNode('E', n4, n5);
treeNode\* n1 = makeRootNode('H', n2, n3);

    printf("전위순회: ");
    preorder(n1);
    printf("중위순회: ");
    inorder(n1);
    printf("후위순회: ");
    postorder(n1);
    printf("레벨순회: ");
    level(n1);

    return 0;

}
{% endhighlight %}
