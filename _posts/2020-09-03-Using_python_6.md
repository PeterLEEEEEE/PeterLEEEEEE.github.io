---
layout: post
title:  "파이썬에서 유용한 기능 정리(2) - Lambda, Map, Filter"
author: Peter
categories: [ Python ]
image: https://user-images.githubusercontent.com/52132160/91701420-3db1f400-ebb2-11ea-8d9e-f11cad524fc0.png



sitemap:
changefreq: daily
priority: 1.0
---
---

- 저번에 이어서 파이썬을 사용하면서 유용하게 사용할 수 있는 기능들을 공유 해 보려고 한다.
지금부터 소개할 세 가지 기능 역시 저번 포스트와 같이 모두 눈으로는 알고 있으나 막상 사용하려면 잘 기억이 안나서 정리했는데 저번보단 확실히 어렵다.

---


---

### 1. map

아래와 같이 숫자로 이루어진 리스트와 숫자의 제곱을 반환하는 square 함수가 있다. 
그런데 여기서 리스트 안의 숫자를 모두 함수롤 통해 제곱으로 바꾸어 주려면 어떻게 해야할까?
![image](https://user-images.githubusercontent.com/52132160/92119827-45cc9680-ee33-11ea-8e30-0bdc75441b98.png)
당장 생각나는 방법은 리스트를 함수로 넘겨 반복문으로 처리하는 방법일 것이다. 하지만 map을 이용하면 훨씬 간단하게 처리 가능하다.
<br><br>
이렇게 map 안에 함수와 리스트를 넣어주면 알아서 처리해준다. **이때 함수는 ()를 작성하지 않는다.**
![image](https://user-images.githubusercontent.com/52132160/92120411-faff4e80-ee33-11ea-87e1-333b46ee7c46.png)
<br>
또한 리스트 값을 출력하고 싶다면 반복문과 map을 함께 사용하면 짧은 코드로 간편하게 출력할 수 있게 된다.
![image](https://user-images.githubusercontent.com/52132160/92120648-4a457f00-ee34-11ea-843e-66f976aec002.png)
<br>

위의 함수와는 다른 string 형태로 구성된 리스트로도 동작이 된다.
![image](https://user-images.githubusercontent.com/52132160/92120965-af00d980-ee34-11ea-89ed-707d1dc81b4e.png)
이처럼 다양한 자료형에서 유연하게 동작하니 유용하지 않을 수 없다!
<br>

---

### 2. Filter


filter는 위에서 설명한 map과 유사하지만 함수의 반환값이 True, 즉 조건에 만족하는 값만 출력하거나 담긴다.
아래 그림을 예시로 들면 리스트에는 1부터 6까지의 정수가 들어있고 even_checker 함수는 말 그대로 인수가 짝수인 것만 반환한다.
![image](https://user-images.githubusercontent.com/52132160/92122210-2125ee00-ee36-11ea-810b-2aece3070e9e.png)
<br><br>

위의 map과 사용법이 일치하는데, 조건에 만족하는 짝수인 2,4,6만 가져오게 된다. 
![image](https://user-images.githubusercontent.com/52132160/92123328-76aeca80-ee37-11ea-8f50-ae8f83ee5884.png)
<br><br>


---
### 3. Lambda 

lambda 는 쉽게 말하면 일회용 함수라고 생각하면 된다. 일반적 함수는 한번 정의해 지속적으로 사용하는데 반해 lambda 함수는 
한번 쓰고 가차없이 버린다.
<br><br>
![image](https://user-images.githubusercontent.com/52132160/92124377-aa3e2480-ee38-11ea-9689-54c4303b69c2.png)
정말 간단하게 위의 함수를 아래처럼 한줄로 완벽하게 똑같이 만들어 버린다.
사실 lambda 함수는 익명 함수이기 때문에 위처럼 square 에 넣어주는 방식으로 사용하지 않고 위에 설명한 map, filter 와 세트로 사용되는 경우가 많다.
<br><br>
아래 그림은 map과 lambda를 조합한 예시이다. 제곱 함수를 구현하지 않고 lambda 로 한줄에 구현하여, 리스트를 map 으로 묶어 반환한다. 
![image](https://user-images.githubusercontent.com/52132160/92125162-a65ed200-ee39-11ea-884a-8de6eb3fa0b5.png)
<br><br>

filter와 lambda 조합, 짝수를 걸러내 리스트를 반환하게끔 만들었다.
![image](https://user-images.githubusercontent.com/52132160/92125924-8c71bf00-ee3a-11ea-8092-b0527949c94b.png)
<br><br>

---

솔직히 위 기능들은 자주 사용해보지 않는 이상 직접쓰려고 하면 난해한 부분이 없지않아 있다. 
그러니 자주 사용해 보는 것을 추천한다. 필자도 일일이 타이밍 해가면서 하는데 이 글을 읽는다면 한번 따라쳐보면서 
따라가보면 좋을 것이다.

---