---
layout: post
title: "Binary Search Tree(BST) - 이진탐색 트리"
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

##### 이진탐색 트리.py

{% highlight python %}

# BST

class Node:
    def __init__(self, data, left = None, right = None):
        self.data = data
        self.left = left
        self.right = right

class Tree:
    def __init__(self, root = None):
        self.root = root

    def insert(self, data):
        self.root = self.insert_val(self.root, data)

    def insert_val(self, node, data):
        if node is None:
           node = Node(data)
           print(node.data)
        else:
            if node.data >= data:
                node.left = self.insert_val(node.left, data)
            else:
                node.right = self.insert_val(node.right, data)

        return node

if __name__ == "__main__": 
    
    # root = [int(x) for x in input().split()] # print(root) 직접 입력

    root = [1,3,5,7,9,11]

    tree = Tree()

    for data in root:
        tree.insert(data)

{% endhighlight %}

---

**참고:**

[파이썬을 이용해서 이진 탐색 트리 구현하기](https://geonlee.tistory.com/72) 

사실 너무 괜찮은 코드라 거의 그대로 가져옴.. 

---
