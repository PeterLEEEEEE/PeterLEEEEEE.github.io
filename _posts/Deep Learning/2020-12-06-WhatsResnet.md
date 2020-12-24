---
layout: post
title: "VGG? ResNet?"
author: Peter
categories: [Deep Learning]
image: https://user-images.githubusercontent.com/52132160/101280874-0e450000-380f-11eb-960d-b70d27b2908c.png

tags: [Deep Learning]
sitemap:
changefreq: daily
priority: 1.0
comments: true
use_math: true
---

<br>
<br>
### Introduction

---

이전 포스트에서 VGG 모델이 잠깐 언급되었는데 VGG 모델의 의의는 기존에 존재하던 모델에 비해 깊은 feature extraction 층을 가지고 있으면서도 정확도가 높다는 점이었다. 여담으로 VGG-16에서의 16은 레이어의 개수를 뜻한다.

다른 차이점은 이전에 존재하던 정확도 높은 모델들은 큰 필터의 $$ 7\times7 $$ 등의 필터를 사용하였으나 VGG 모델은 $$ 3\times3 $$의 작은 필터만을 사용하였음에도 기존보다 더 높은 정확도를 보여준다.

예시로 $$ 10\times10 $$ 의 이미지(흰색 바탕)에 $$ 7\times7 $$ 필터를 사용하여 convolution 연산을 하게되면 output의 feature map 1 pixel($$ 4\times4 $$ 사각형의의 노란색 사각형 한 개)은 본래의 이미지의 $$ 7\times7 $$ 만큼의 정보를 담는다.(그리고 이를 **receptive field**라고 한다).

![image](https://user-images.githubusercontent.com/52132160/101345628-aeac2a80-38ca-11eb-8ecc-b51b36640af2.png)

하지만 $$ 3\times3 $$ convolution 연산을 3번 수행하게 되면 $$ 7\times7 $$ 연산을 한번 수행한 것과 같은 receptive field를 가진다.(아래 그림의 빨간색 사각형 부분을 잘 살펴보면 된다.)
![image](https://user-images.githubusercontent.com/52132160/101346747-5b3adc00-38cc-11eb-9c1c-5f742e3f2ebb.png)

출처: [강준영 님의 VGG16 논문 리뷰 — Very Deep Convolutional Networks for Large-Scale Image Recognition](https://medium.com/@msmapark2/vgg16-%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-very-deep-convolutional-networks-for-large-scale-image-recognition-6f748235242a)

이러한 연산의 장점은 첫째, convolution 층을 많이 쌓으면서 사용하게 되는 ReLU 함수로 인해 비선형성이 증가하며 사진의 특징을 더 잘 구분하도록 하는 장점이 있다. 두 번째는 파라미터 수의 감소에 있다. 필터의 크기 = 파라미터의 크기이니 대충 계산해봐도 파라미터 수가 거의 2배 가까이 감소하였음을 알 수 있다.

<br>
<br>

### 깊게 더 깊게, VGG의 문제점

---

VGG 모델에 대한 내용을 3줄 요약해보자면,

- 작은 사이즈의 필터로 높은 정확도(적은 파라미터 사용으로 높은 정확도 도출)
- 높은 정확도 대비 비교적 단순한 모델
- 깊은 feature extraction layer의 사용으로 인한 특징 추출 용이
  정도를 꼽을 수 있다.
  <br>
  하지만 여기서 문제점이 존재하는데 VGG는 레이어를 19층 이상 쌓게되면 더 이상 정확도가 증가하지 않고 overfitting이 된다는 점이다.
  (그래서 VGG-19까지 존재한다)

아니 앞에서 깊게 쌓으면 쌓을수록 좋다고 하였는데 19층? 바로 여기서 VGG 모델의 한계점이 드러난다. VGG 모델을 19층 이상으로 쌓게되면 2가지 문제점이 발생하게 되는데, 첫 번째는 어쨋든 파라미터 수를 줄이긴 했지만 망이 깊어지면 깊어질수록 결국에 파라미터 수는 기하급수적으로 증가한다는 점이다. 결국 파라미터 수의 증가는 컴퓨팅 자원을 많이 요구하게 되고 처리 속도도 느려지게 된다.

![image](https://user-images.githubusercontent.com/52132160/101353258-a1953880-38d6-11eb-9f45-3637f893d999.png)

<br>
<br>

### 해결사 ResNet

---