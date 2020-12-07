---
layout: post
title: "overfitting(과적합) 문제"
author: Peter
categories: [Deep Learning]
image: https://user-images.githubusercontent.com/52132160/101383684-c9979280-38fc-11eb-89a8-d06689c97408.png

tags: [Deep Learning]
sitemap:
changefreq: daily
priority: 1.0
comments: true
use_math: true
---

<br>
<br>

### overfitting, underfitting

---

![image](https://user-images.githubusercontent.com/52132160/101383851-06638980-38fd-11eb-8998-6743ac34f34c.png)

- **이상적 학습**: Low Variance, Low Bias
- underfitting: Low Variance, High Bias
- overfitting: High Variance, Low Bias

<br>
<br>

### Underfitting 해결법

---

- feature를 더 수집한다.
- Variance가 높은 모델을 사용한다.

<br>
<br>

### Overfitting 파악 및 해결법

---

- Training error 보다 test error 눈에 띄게 높을 때 (학습한 데이터는 정확도가 높으나, 새로운 데이터에 대한 정확도가 낮음)

이를 쉽게 알 수 있는 방법은 **Validation Dataset**를 중간 검증용으로 놓는 것이다(최종 검증은 test data에서의 정확도이라 중간 검증이라 표현하였다).

예를 들어 학습 데이터가 100개 존재하면 그 중 20개를 validation data로 잘라놓고 학습에 참여하지 않는다. 이렇게 validation 정확도를 측정하고 train 정확도보다 현저하게 낮다면 이는 overfitting이라 판단할 수 있기에 학습 모델에 **변화**를 주어 이를 낮추어야 한다.
<br>
<br>

아래 사진처럼 구분해볼 수 있다.
![image](https://www.brainstobytes.com/content/images/2020/01/Sets-1.png)

    source: www.brainstobytes.com/test-training-and-validation-sets

주로 **overfitting**이 일어나는 경우는

- 모델이 매개변수가 많을 때
- 훈련 데이터가 적을 때

<br>

이기 때문에 학습 중 위와 같은 현상이 발생한다면, 이를 해결하기 위해 아래과 같은 방법들을 고려해볼 수 있다.

- **Data Augmentation**을 통한 데이터 양을 늘리는 방법
- 매개변수를 줄이기 위해 모델의 레이어를 제거하는 방법
- **dropout** 설정을 통한 파라미터의 제거
- 큰 가중치에 대해서 그에 맞는 보정을 주는 **가중치 감소 기법**

<br>

여기서 본인의 데이터와 모델을 감안하여 위와 같은 수정을 거친다면 보다 높은 정확도를 가진 모델을 만들어낼 수 있을 것이다.

<br>
<br>

---
