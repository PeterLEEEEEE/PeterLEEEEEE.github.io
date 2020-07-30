---
layout: post
title:  "우선순위 큐(Priority Queue)와 힙(heap)"
author: peter
categories: [ DataStructure ]
image: assets/images/1.jpg
tags: 
sitemap:
changefreq: daily
priority: 1.0
---
---

### 우선순위 큐(Priority Queue)
기존의 선입선출(FIFO) 방식인 큐(queue)와는 달리 우선순위가 높은 데이터부터 나오는 구조.
이 우선순위는 사용자가 정한다.


##### 구현 방법
1. 배열(array)을 이용한 구현
2. 연결 리스트(linked list)를 이용한 구현
3. 힙(heap)을 이용한 구현 

배열과 연결 리스트를 이용하면 손쉽게 우선순위 큐를 구현할 수 있지만 각각 명확한 단점이 존재하는데,
- **배열**은 기본적으로 데이터의 삽입 및 삭제 시 기존에 존재하던 데이터를 밀어내거나 당겨와야 한다. 즉 데이터가 많아지면 그 단점은 더욱 두드러지게 된다.

- **연결 리스트**는 모든 노드에 접근해가며 비교 연산을 해야 한다는 점에서 역시나 데이터가 많아지면 단점을 보이게 된다.

--- 

|표현 방법|삽입|삭제|
|:------------------:|:------:|:----:|
|순서없는 배열    |O(1)|O(n)|
|순서없는 연결리스트  |O(1)|O(n)|
|정렬된 배열|O(n)|O(1)|
|정렬된 연결 리스트|O(n)|O(1)|
|<span style="color:red">힙(heap)</span>|O(logn)|O(logn)|  

---
>
> 위 표처럼 **힙(heap)**을 사용하여 구현하는 것이 가장 효율적이다. 

---

### 힙(heap)

힙(heap)이란 완전 이진트리의 한 종류로 우선순위 큐를 위해 만들어진 자료구조이다.


##### 특징
1. 여러 개의 값들 중에서 최대값이나 최솟값을 빠르게 찾아내는 것이 가능하다(최대 힙, 최소 힙)
2. 부모 노드과 자식 노드과의 상-하 관계가 존재하지만 자식 노드(좌-우)간에 관계는 없다(반정렬 상태)
3. 이진 탐색 트리와는 다르게 **중복 값**도 허용. 
4. 노드 A[n]의 왼쪽, 오른쪽 자식노드와 부모노드의 인덱스를 O(1) 시간에 연산


##### 종류
1. 최대 힙(Max Heap)
    - 부모 노드 키 값 >= 자식 노드 키 값 ==> 루트 노드 최대값

2. 최소 힙(Min Heap)
    - 부모 노드 키 값 <= 자식 노드 키 값 ==> 루트 노드 최소값

---

##### 구현
- 구현은 보통 **배열**을 이용하여 구현한다.
- 구현의 편의성을 위해 배열의 0번 째 인덱스는 비워놓고 1번 인덱스부터 추가한다(1번 = 루트 노드의 키)
- 부모 노드와 자식 노드의 인덱스 
    - parent_index = left or right_child / 2
    - left_child = parent_index * 2 
    - right_child = (parent_index * 2) + 1

![힙구조](https://user-images.githubusercontent.com/52132160/88613954-a4cb1d00-d0c9-11ea-9b70-442693baf50c.PNG)

---
##### heap.c

{% highlight cpp %}
#define MAX 100

typedef struct {
    int key;
}element;

typedef struct {
    element heap[MAX];
    int heap_size;
}HeapType;

HeapType* heap = create() // 동적 메모리 할당 

// 힙 생성
HeapType create(){
    return (HeapType*)malloc(sizeof(HeapType));
}

// 초기화
void init(HeapType* h){
    h->heap_size = 0;
}

// 힙의 삽입(힙에 새로운 요소가 들어오면, 마지막 노드에 붙이고 정렬)
void insert_max_heap(HeapType* h, element item){
    int i;
    i = ++(h->heap_size);
    
    // 트리를 올라가며 부모 노드와 비교
    while((i != 1) && (item.key > h->heap[i/2].key)){
        h->heap[i] = h->heap[i/2];
        i /= 2;
    }
    h->heap[i] = item; // 새로운 노드 삽입 
}

// 힙의 삭제(연산 O(logn)) 
// 루트 노드 삭제 -> 마지막 노드를 루트 노드로 이동 -> 루트에서부터 단말 노드까지 경로에 있는 노드들을 교환(정렬)

element delete_max_heap(HeapType* h){
 int parent, child;
 element item, temp;
 
 item = h-> heap[1];
 temp = h->heap[(h->heap_size)--];
 parent = 1;
 child = 2;
 while(child <= h->heap_size){
    // 현재 노드의 자식노드 중 더 큰 자식노드를 찾음
    if((child < h->heap_size) && (h->heap[child].key) < h->eheap[child+1].key){
        child++;
    }
    if(temp.key >= h->heap[child].key) break;
    // 아래 단계로 이동
    h->heap[parent] = h->heap[child];
    parent = child;
    child *= 2;
 }
 h->heap[parent] = temp;
 return item;
}

int main() {
	element e1 = { 10 };
	element e2 = { 5 };
	element e3 = { 30 };
	element e4, e5, e6;

	HeapType* heap;

	heap = create(); // 힙 생성
	init(heap); // 초기화

    //삽입
	insert_max_heap(heap, e1);
	insert_max_heap(heap, e2);
	insert_max_heap(heap, e3);
    
    //삭제
	e4 = delete_max_heap(heap);
	printf("%d\n", e4.key);
	e5 = delete_max_heap(heap);
	printf("%d\n", e5.key);
	e6 = delete_max_heap(heap);
	printf("%d\n", e6.key);

	free(heap);

	return 0;
}


{% endhighlight %}
---

---