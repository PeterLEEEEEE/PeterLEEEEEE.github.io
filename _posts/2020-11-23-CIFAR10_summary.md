---
layout: post
title: "딥러닝 - CIFAR-10 모델 구현 by keras(colab)"
author: Peter
categories: [Deep Learning]
image: https://user-images.githubusercontent.com/52132160/99202726-7053ac00-27f3-11eb-8ce4-2c3be45146c2.png

sitemap:
changefreq: daily
priority: 1.0
---

---

### CIFAR-10

<p>
CIFAR-10은 32x32 픽셀 사이즈의 RGB를 가진 이미지들의 데이터 셋으로 종 10가지 종류 6만장의 이미지로 이루어진 데이터 셋이다.

</p>

![image](https://user-images.githubusercontent.com/52132160/99909503-3d964000-2d2c-11eb-9c79-b261c7f2fdb9.png)

        source: https://www.cs.toronto.edu/~kriz/cifar.html

---

### 데이터 전처리

<p>
전처리에 앞서 필자는 colab을 사용한다. 노트북 밖에 없고 데스크탑 사양이 좋지 않은 필자 같은 분들은 colab을 사용하는 것을 권장한다.(ipynb 환경이라 다운도 편하고 노트북 용량도 차지하지 않으니 좋다)

우선 데이터를 다운 받는 것이 제일 먼저다.

</p>

{% highlight python%}

from keras.datasets import cifar10
import numpy as np
import matplotlib.pyplot as plt
from keras.utils.np_utils import to_categorical
import tensorflow as tf
import keras
import random

{% endhighlight %}

우선은 앞으로 필요한 라이브러리를 이렇게 가져와 놓겠다. 여기서 cifar-10 데이터 셋을 다운받기 위해서는 첫째 줄에 있는 **from keras.datasets import cifar10** 요녀석을 꼭 써주어야 한다.
