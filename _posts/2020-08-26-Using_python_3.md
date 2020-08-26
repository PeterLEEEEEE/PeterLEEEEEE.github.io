---
layout: post
title:  "파이썬에서 자주 혼동되는 내용 정리(3)"
author: Peter
categories: [ Python ]
image: https://user-images.githubusercontent.com/52132160/91169688-b88e9100-e712-11ea-9bf5-2e45542d41c6.png

sitemap:
changefreq: daily
priority: 1.0
---
---

### 튜플(Tuple)

**튜플**은 **수정이 불가능**하다는 점을 제외하고는 모두 리스트가 같은 특성을 가지고 있다. 

**튜플은 수정이 되질 않는다**
![image](https://user-images.githubusercontent.com/52132160/91326939-e30a4800-e7ff-11ea-8647-a127a2e989d0.png)
이는 나중에 내가 본의 아니게 값을 수정하는 실수를 막아주는데 유용하다.
<br><br>

**count를 이용한 원소 세기**
![image](https://user-images.githubusercontent.com/52132160/91326396-421b8d00-e7ff-11ea-877b-531f57a74955.png)
<br><br>

**index를 이용하여 내가 찾는 원소 위치 파악**
![image](https://user-images.githubusercontent.com/52132160/91326590-78f1a300-e7ff-11ea-807d-9e8aabafbcff.png)
'abc'는 0, 1번 인덱스에 존재하지만 가장 앞에 있는 인덱스만 찾아서 반환한다.
<br><br>

---

### 집합(Sets)

**집합**은 **순서가 없고** 값이 중복되지 않은 **unique** 한 값들의 모임이다. 
<br><br>

**집합의 선언과 추가**
![image](https://user-images.githubusercontent.com/52132160/91327732-e5b96d00-e800-11ea-8326-763edba614e7.png)
<br><br>

**중복된 값을 추가할 경우**
![image](https://user-images.githubusercontent.com/52132160/91327877-18fbfc00-e801-11ea-8ecb-d6a17b36fc90.png)
중복된 값은 추가가 이루어지지 않는다.
<br><br>

---

### Booleans

**Booleans**는 **True** 혹은 **False**로 구성된 연산자인데 나중에 흐름제어나 논리에서 유용하게 사용된다. 
<br><br>

**파이썬에서는 맨앞을 대문자로 써주어야 한다**
![image](https://user-images.githubusercontent.com/52132160/91328818-58771800-e802-11ea-9e8b-4e36cdd44876.png)
<br><br>


---
