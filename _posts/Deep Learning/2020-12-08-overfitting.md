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
- underfitting: Low Variance, High Bias **(High Bias 문제)**
- overfitting: High Variance, Low Bias **(High Variance 문제)**

Bias 문제인지 Variance 문제인지 파악하는 방법은 cross validation error 값과 training error를 비교하는 방법인데, 값이 모두 크면서 그 차이가 크지 않다면 High Bias 문제라고 볼 수 있고 cross validation error의 크기는 크지만 training error는 작아 둘의 차이가 크다면 High Variance 문제라고 볼 수 있다.

<br>
<br>

![image](https://user-images.githubusercontent.com/52132160/103076933-2770ed80-4612-11eb-90e8-0427d490a58c.png)

        source: Machine Learning by Andrew Ng (https://www.coursera.org/learn/machine-learning)

<br>
<br>

### Underfitting의 이유와 해결법

---

Underfitting은 모델이 너무 간단하거나 데이터 부족으로 학습이 제대로 되지 않는 현상을 말한다. 이러면 모델 정확도가 낮기에 validation loss와 test loss 모두 매우 높을 것이다.

이에 대한 해결법은 직관적으로 데이터를 더 수집하거나 더 표현력이 높은 즉 Variance가 높은 모델을 통해 학습시키면 된다.

요약하자면

- 데이터를 더 수집한다.
- Variance가 높은 모델을 사용한다.(조금 더 복잡한 모델을 사용)

<br>
<br>

### Overfitting의 이유

---

**overfitting**이 일어나는 경우는 2가지로 나누어 볼 수 있는데,

- 모델이 매개변수가 많을 때(모델 복잡도가 높음)
- 훈련 데이터가 적을 때

모델이 복잡하다는 말과 매개변수가 많다는 말은 결과적으로 같은 뜻이다. 고차원의 다항함수은 그 차원이 높아질수록(복잡) 더 많은 파라미터를 가지게 되고 그만큼 Train dateset에서는 잘 동작하지만 실제 적용되는 데이터에서는 만족스러운 정확도를 얻지 못하게 된다. 그러므로 적절하게 복잡한 최적의 모델을 선택하는 것이 항상 중요하다.

두 번째는 단순히 데이터가 너무 적은 문제이다. 모델이 복잡한 만큼 그에 상응하는 데이터를 학습시킬 수 있어야 한다. 이 밸런스가 무너지면 오버피팅이 발생하게 된다.

<br>
<br>
<br>

### Overfitting 파악 및 해결법

---

- Training error 보다 test error 눈에 띄게 높을 때 (학습한 데이터는 정확도가 높으나, 새로운 데이터에 대한 정확도가 낮음)

이를 쉽게 알 수 있는 방법은 **Validation Dataset**를 중간 검증용으로 놓는 것이다(최종 검증은 test data에서의 실전 정확도이라 중간 검증이라 표현하였다).

예를 들어 학습 데이터가 100개 존재하면 그 중 20개를 validation data로 잘라놓고 학습에 참여하지 않는다. 이렇게 validation 정확도를 측정하고 train 정확도보다 현저하게 낮다면 이는 overfitting이라 판단할 수 있기에 학습 모델에 **변화**를 주어 이를 낮추어야 한다.
<br>
<br>

아래 사진처럼 구분해볼 수 있다.
![image](https://www.brainstobytes.com/content/images/2020/01/Sets-1.png)

    source: www.brainstobytes.com/test-training-and-validation-sets

<br>

때문에 학습 중 위와 같은 현상이 발생한다면, 이를 해결하기 위해 아래과 같은 방법들을 고려해볼 수 있다.

1.  **Data Augmentation**을 통한 데이터 양을 늘리는 방법
2.  매개변수를 줄이기 위해 모델의 레이어를 제거하는 방법
3.  큰 가중치에 대해서 그에 맞는 보정을 주는 **가중치 감소 기법**(\*Regularization)
4.  **dropout** 설정을 통한 파라미터의 제거
    <br>
    <br>

        * 모델이 학습된 데이터가 아닌 새로운 데이터에 대해 정확한 예측이 가능하면 이를 일반화(Regularization)되었다고 칭한다.

   <br>

여기서 본인의 데이터와 모델을 감안하여 위와 같은 수정을 거친다면 보다 높은 정확도를 가진 모델을 만들어낼 수 있을 것이다.

<br>
<br>

---
