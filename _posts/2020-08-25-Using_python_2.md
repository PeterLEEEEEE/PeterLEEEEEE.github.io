---
layout: post
title:  "파이썬에서 자주 혼동되는 내용 정리(2)"
author: Peter
categories: [ Python ]
image: assets/images/2.jpg
---
---

### 리스트에 대한 정리 

**리스트**는 이전 포스트에서도 언급 하였다시피 **순서가 있고(고로 인덱싱이 가능) 수정이 가능한 자료형**이다.
이를 이용해 다양한 작업이 가능한데 배우고도 금방 기억에서 삭제되는 내용들을 몇가지 정리해 보았다.
<br><br>

**리스트를 활용한 덧셈 연산**
![image](https://user-images.githubusercontent.com/52132160/91143275-35a70f80-e6ed-11ea-9fd5-7b686e39bb34.png)
<br>

**인덱스를 이용하여 리스트 수정**
![image](https://user-images.githubusercontent.com/52132160/91143392-6a1acb80-e6ed-11ea-9ba2-a1c69baac620.png)
<br>

**append를 활용한 리스트 삽입**
![image](https://user-images.githubusercontent.com/52132160/91143521-a0584b00-e6ed-11ea-8315-36a5dde2437d.png)
<br>
**pop을 활용한 리스트 삭제1**
![image](https://user-images.githubusercontent.com/52132160/91143705-e7464080-e6ed-11ea-8c70-3ec624ac752c.png)
<br>
**pop을 활용한 리스트 삭제2(인덱스 사용)**
![image](https://user-images.githubusercontent.com/52132160/91143924-3b512500-e6ee-11ea-981a-c5e8d17584cd.png)
<br>

**sort함수를 사용한 리스트 정렬**
![image](https://user-images.githubusercontent.com/52132160/91146752-47d77c80-e6f2-11ea-853b-844d9599f85b.png)
여기서 알아두어야 할 점은 함수를 사용한 리턴 값을 바로 변수에 할당하려 하면 None이 반환되기 때문에 sort 함수를 호출하고 그 다음에 할당 해주어야 올바르게 값이 들어간다.
<br><br>

**reverse를 활용한 리스트 역순**
![image](https://user-images.githubusercontent.com/52132160/91147149-d2b87700-e6f2-11ea-8d5d-c1daf26880a2.png)
<br>

---

### 딕셔너리에 대한 정리

**딕셔너리**는 순서가 없는 대신에 key-value 쌍으로 이루어져 있다. 사용자는 인덱스 번호를 알 필요없이 **키 값**으로 원하는 값을 찾을 수 있는 자료형이다.<br>

**참고**: 키 값은 항상 **str형** 이어야 한다(''로 감싸줘야 함), 순서가 없다
<br><br>

**기본적인 딕셔너리 선언1**
![image](https://user-images.githubusercontent.com/52132160/91152707-46aa4d80-e6fa-11ea-885b-89138ffe33a2.png)
<br><br>

**기본적인 딕셔너리 선언2**
![image](https://user-images.githubusercontent.com/52132160/91152817-6772a300-e6fa-11ea-8a02-2a1f4b065260.png)
<br><br>

**딕셔너리 삽입**
![image](https://user-images.githubusercontent.com/52132160/91154148-1c598f80-e6fc-11ea-9d17-9158b9e4662a.png)
<br><br>

**딕셔너리 수정**
![image](https://user-images.githubusercontent.com/52132160/91154372-6a6e9300-e6fc-11ea-98d6-217a9b5a4ffd.png)
딕셔너리도 리스트와 같이 value 값 수정이 가능하다.
<br><br>

**키 값과 밸류 값 한번에 받아오기(keys, values, items)**
![image](https://user-images.githubusercontent.com/52132160/91154605-aace1100-e6fc-11ea-96c1-5c10fd932e5c.png)
![image](https://user-images.githubusercontent.com/52132160/91154825-f1237000-e6fc-11ea-9f9b-147cc5eb2192.png)
items를 사용하면 튜플형으로 반환된다.
<br><br>

**유연성이 높은 딕셔너리(value 값을 유연하게 받을 수 있다)**
![image](https://user-images.githubusercontent.com/52132160/91152985-9721ab00-e6fa-11ea-9c0a-662cd416c4e3.png)
여기서 주목해야 할 점은 딕셔너리의 value 값으로 딕셔너리를 받을 수 있는데(위 내용의 key3), 그 안의 key 값을 받으려면 위와 같은 방식을 사용한다.
<br><br>

![image](https://user-images.githubusercontent.com/52132160/91153501-41013780-e6fb-11ea-98de-e0c7f0813ec3.png)
마찬가지로 key2에서 리스트를 받았는데, 리스트 인덱스를 입력하면 그 값을 받아오는 것도 가능하다.
<br><br>


---


