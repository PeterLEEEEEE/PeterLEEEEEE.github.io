---
layout: post
title: "Cross Entropy의 종류들(sparse cross entropy, binary cross entropy)"
author: Peter
categories: [Deep Learning]
image: https://user-images.githubusercontent.com/52132160/100248630-0ec3d800-2f7f-11eb-9cc3-db0f10ae26eb.png

tags: [Deep Learning]
sitemap:
changefreq: daily
priority: 1.0

use_math: true
---

---

정말 간단하게 수식없이 어느 상황에서 loss function을 사용해야할 지 적어보도록 하겠다.

---

### Binary Cross Entropy

Binary Cross Entropy 는 multi-label classification에서 사용하지만 **2-class**(true, false 혹은 0, 1 등등)의 제한적인 형태에서 사용된다.
모델에서 정의할 때 마지막에 dense를 **2**로 해주어야 한다.
그렇지 않으면 에러가 뜨니까 꼭 모델 만들 때 모든 레이어를 쌓고 마지막에 두 가지 갈래로 나오게끔 만들면 된다.

---

### Categorical Cross Entropy

Categorical Cross Entropy는 데이터 label이 원-핫 인코딩 방식일 때 사용한다.
우리가 to_categorical을 죽어라 사용하는 것도 이것 때문일 확률이 높다.

---

### Sparse Categorical Cross Entropy

Sparse Categorical Cross Entropy는 반대로 label이 정수일 때 사용한다. 기본적으로 데이터 셋이 제공될 때 label이 정수 형태를 띄고 있는 경우가 많은데 이럴 때 이 loss function을 사용한다.

---

보완 수정 필요..
