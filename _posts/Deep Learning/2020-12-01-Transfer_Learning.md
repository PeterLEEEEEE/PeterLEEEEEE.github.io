---
layout: post
title: "Transfer Learning"
author: Peter
categories: [Deep Learning]
image: https://user-images.githubusercontent.com/52132160/100248630-0ec3d800-2f7f-11eb-9cc3-db0f10ae26eb.png

tags: [Deep Learning]
sitemap:
changefreq: daily
priority: 1.0
comments: true
use_math: true
---

---

Introduction

---

Transfer Learning, 한국말로 **전이학습** 이라 불리는 방법은 이미지 처리에서 높은 정확도를 보여주는 학습 방법이다.
cifar-10에서 직접 만든 모델로 정확도를 측정하였을 때, 80%에 미치지 못하는 정확도를 보여주었고 여러 방면으로 시도 해보아도 쉽지 않은 과정이었다.
그러나 전이학습을 통해 90% 대의 정확도를 낼 수 있다는 얘기를 들었고 궁금증을 이기지 못하여 직접 찾아보게 되었다.

---

### Transfer Learning

전이학습은 단기간 내에 높은 정확도를 낼 수 있다고 한다. 전이학습을 통해 나처럼 직접 모델을 한 층씩 만들지 않고 이미 학습된 weight와 bias를 통해 다양한 분류 문제에 적용할 수 있다. 이미지 처리에서의 전이학습은 pre-trained model 즉 이미 학습된 모델을 이용하는 것이라고 한다. pre-trained model은 대량의 데이터를 통해 이미 학습이 되어 있는 모델이다. 예를 들면 VGG 모델은 애초에 classification label이 1000개일 정도로 엄청난 데이터 수를 자랑한고 그렇게 많은 데이터를 학습시킨다는 건 너무나도 많은 시간이 필요하기에 공개된 모델을 import해서 사용한다.

---

### Categorical Cross Entropy

Categorical Cross Entropy는 데이터 label이 원-핫 인코딩 방식일 때 사용한다.
우리가 to_categorical을 죽어라 사용하는 것도 이것 때문일 확률이 높다.

---

### Sparse Categorical Cross Entropy

Sparse Categorical Cross Entropy는 반대로 label이 정수일 때 사용한다. 기본적으로 데이터 셋이 제공될 때 label이 정수 형태를 띄고 있는 경우가 많은데 이럴 때 이 loss function을 사용한다.

---

보완 수정 필요..
