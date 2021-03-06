---
layout: post
title:  "월간 데이콘7 - 글자에 숨겨진 숫자 이미지 예측(MNIST)"
author: Peter
categories: [ Deep Learning ]
image: https://user-images.githubusercontent.com/52132160/91169688-b88e9100-e712-11ea-9bf5-2e45542d41c6.png

sitemap:
changefreq: daily
priority: 1.0
---
---

이번에 데이콘에서 MNIST 관련하여 재밌는 대회가 있어서 참가하게 되었다. 내용은 글자에 숨겨진 숫자 이미지를 예측하는 것으로 기존 MNIST 안에 숫자를 집어넣어 이를 학습하고 예측하는 대회이다. 

그럼 이제 코드 하나하나 뜯어보며 복습해보는 시간을 갖도록 하겠다. 
사용 환경은 colab으로 작성하였다.

### 데이터 전처리 

우선 아래와 같이 필요한 라이브러리를 불러온다.
 ![image](https://user-images.githubusercontent.com/52132160/92950805-46e76e80-f498-11ea-8899-78ad95fb2fe8.png)
<br><br>

다음은 대회에서 제공하는 데이터인 train.csv와 test.csv를 가져와서 데이터가 어떻게 구성되어 있는 지 파악해볼 것이다. 둘 다 csv 파일로 pandas를 사용하여 쉽게 가져올 수 있다. 
![image](https://user-images.githubusercontent.com/52132160/92951060-ba897b80-f498-11ea-8d54-7ba55ed6e834.png)
.shape을 활용해 데이터 구성을 볼 수 있다. train 데이터는 2048장의 이미지를 test 데이터는 20480장으로 train 데이터의 10배가 된다.(786과 785는 가로,세로 픽셀 + letter, digit column)
<br><br>

그래도 혹시 몰라 .head를 이용해 상위 5개의 데이터를 찍어보았고 아래 사진과 같이 구성되어 있음을 알 수 있었다. test 데이터는 digit이 없어 가로 1 차이가 있다.
![image](https://user-images.githubusercontent.com/52132160/92952393-daba3a00-f49a-11ea-9c6e-e4272365643e.png)
<br><br>

letter와 digits의 구성이 궁금하여 이렇게 중복을 제거하여 표시했다.
대문자로 되어있는 막상 이미지 데이터는 소문자도 있다.
![image](https://user-images.githubusercontent.com/52132160/92952665-5320fb00-f49b-11ea-9419-fa83b6a90c3a.png)
<br><br>

이제 pyplot으로 간단하게 <2, 2> 로 이미지를 나타내보았다. 무작위로 4장을 뽑았고 이미지가 가로, 세로가 아닌 일직선으로 쭉 나열되있는 형태여서 직접 28,28 로 reshape을 해주었다. (기본적으로 MNIST 이미지는 가로세로 28x28이다.)
![image](https://user-images.githubusercontent.com/52132160/92952899-b448ce80-f49b-11ea-8d9f-e4c7b38344c1.png)
여기서 숫자가 겹쳐있는 부분이 다른 부분에 비해 밝은 것을 알 수 있다(사실 알파벳은 그냥저냥 육안으로 파악 가능한데 안에 숫자는 도저히 알 길이 없다).
<br><br>

데이터가 어떻게 생겼는 지도 확인하였고 이제는 불필요한 요소들을 제거하여 오로지 이미지만을 담고있는 변수를 만들어준다. 
![image](https://user-images.githubusercontent.com/52132160/92953128-21f4fa80-f49c-11ea-9494-f75266b75a50.png)
<br>

여기서 중요한게 loc을 사용했는데 iloc이랑 항상 까먹어서 여기 남긴다.
위 문장을 해석하면 모든 행에서 column '0'에서부터 끝까지 reshape을 해주는데 28, 28에서 한 차원을 추가하여 (28, 28, 1)로 변환. 1의 역할은 RGB인데 컬러는 3 이어야 하지만 흑백은 1이다. 
![image](https://user-images.githubusercontent.com/52132160/92953598-f32b5400-f49c-11ea-8101-f6e85a02bc41.png)
<br><br>

그래서 총 2048장의 (28, 28, 1) 형태로 x_train에 담기게 되었다.
![image](https://user-images.githubusercontent.com/52132160/92954005-aac06600-f49d-11ea-963b-2df058171488.png)
<br><br>

여기서부터 이제 생각을 해야하는데, 학습데이터는 2048개지만 테스트 데이터는 이에 10배가 많다 즉 데이터를 늘려야 학습을 하는데 있어서 효과가 있을 것이다. 
그런데 이를 손쉽게 도와주는 keras 라이브러리가 있어서 사용해 보았다. 

**여러 방법을 사용하여 데이터 증식을 해보았으나 회전이 그나마 효과가 있어서 사용했다.**
![image](https://user-images.githubusercontent.com/52132160/92954465-726d5780-f49e-11ea-9ab2-71ef015e01b6.png)
주석처리 한 부분은 확대,축소 기능이다. 
사실 눈에 확 띌 정도의 정확도 향상이 없었는데 아무래도 알파벳이기 때문에 조금만 변형이 일어나도 제대로 학습이 되지 않기 때문인 것 같다.
<br><br>

train_list는 digit 정보만 담긴 리스트인데 후에 y_train 에 쓰일 친구지만 다음에 덮어씌울 것이라 신경안써도 된다. 그리고 x_train을 형변환해주어야 concat이 가능해 해주었다.
![image](https://user-images.githubusercontent.com/52132160/92954722-e60f6480-f49e-11ea-8ad4-8cceccaa9bca.png)
<br><br>

전체에서 가장 어려웠던 부분이다. x_train의 이미지 수 만큼 반복문을 돌며 x_train의 뒤에 새로 생성된 이미지를 추가 해주는데 이게 concat을 하려면 자료형과 차원이 맞아야 하다보니 이렇게 복잡한 코드가 만들어졌다. 요는 expand_dims로 차원을 4차원으로 늘려주어 x_train(4차원)에 추가한 다음 정답을 train_list에 append하는 형태이다. 
그리고 to_categorical을 사용하여 원-핫 인코딩(정답 1, 오답 0)으로 만들어 y_train에 추가한다. 
![image](https://user-images.githubusercontent.com/52132160/92954960-4dc5af80-f49f-11ea-8250-22a551163e6c.png)
<br><br>

x_train의 이미지 수는 기존의 약 10배 추가되었고, 답안지인 y_train도 잘 만들어 졌음을 확인해볼 수 있다.
![image](https://user-images.githubusercontent.com/52132160/92955467-228f9000-f4a0-11ea-8abf-9c116f31fd6c.png)
<br><br>

---

### 시각화 및 모델 생성

자 이제 데이터 증식이 잘 되었는 확인을 해볼 겸 아까 사용했던 pyplot를 활용하여 시각화 해 보았다. 
![image](https://user-images.githubusercontent.com/52132160/92993381-16511480-f52c-11ea-80ec-5116ef82a622.png)
자세히보면 글자가 미세하게 기울어있다.
<br><br>

모델은 아래와 같이 작성하였는데, 이미지 형태가 (28, 28, 1) 그리고 필터 사이즈는 (3, 3)의 32장을 사용하였고 중간중간 batch normalization을 통해 학습하였다. 주석처리된 Global Average Pooling도 시도해보았으나 기존에 비해 정확도가 눈에 띄게 떨어져 사용하지 않게 되었다.
![image](https://user-images.githubusercontent.com/52132160/92993508-14d41c00-f52d-11ea-9fba-e0f09e521ba8.png)
<br><br>

데이터를 순서대로 증식하였기에 임의로 섞어주었고 batch size = 32 즉 32장의 이미지를 보고 한번 판단(역전파 시행), epoch = 25 전체 데이터를 25번 보게끔 함으로서 학습 처리하였다. 
![image](https://user-images.githubusercontent.com/52132160/92993627-09cdbb80-f52e-11ea-8ac6-f7c230a4ba9a.png)
<br><br>

이런 결과물이 나왔고 제출 결과 0.92의 정확도를 얻게 되었다. 
![image](https://user-images.githubusercontent.com/52132160/92993685-852f6d00-f52e-11ea-930c-d2fcc0510b42.png)
<br><br>

---

### 후기 

사실 처음에 모델을 작성하였을 때, 이전에 하였던 fashion MNIST에서 사용한 모델을 참고하여 사용했었는데 그동안 수정하였던 어떤 모델보다 정확도가 높게나와서 심히 당황스러웠고, Data augumentation과 Batch Normalization으로 정확도를 늘릴 수 있다고 들었는데 오히려 정확도가 떨어지는 기이한 현상을 목격할 수 있었다(데이터가 단순 사물이 아닌 글자, 숫자를 판독하는 부분이라 그럴지도). 정말이지 쉽지 않다...




---
