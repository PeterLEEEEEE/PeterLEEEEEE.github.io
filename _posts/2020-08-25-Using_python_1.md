---
layout: post
title:  "파이썬에서 자주 혼동되는 내용 정리(1)"
author: Peter
categories: [ Python ]
image: https://user-images.githubusercontent.com/52132160/91168615-e246b880-e710-11ea-98cd-8548c0686ef5.png

sitemap:
changefreq: daily
priority: 1.0
---
---

### 파이썬의 자료형 

파이썬은 실제로 다른 프로그래밍 언어와는 다르게 자료형을 입력하진 않지만 그렇다고 해서 자료형이 없는 것은 아니다.
이에 혼동하지 않도록 자료형을 정리해 보았다.

*Integer(int)*: 1, 300, 500 등의 정수
<br><br>

*Floating point*(float): 1.3, 2.2 와 같은 소수점을 포함한 숫자
<br><br>

*String(str)*: 글자의 unicode로 이루어진 순서있는 집합, 'hi', 'pineapple' 등
<br><br>

*list*: **순서가 있는 수정가능한** 객체의 집합([1,'a', True]와 같은 모습)
<br><br>

*Tuple(tup)*: **순서가 있는 불변한** 객체의 집합, (1, 'a') 와 같이 표시.
<br><br>
 
*Dictionary(dict)*: 불변한 키(key)와 수정가능한 값(value)로 매핑된 **순서가 없는** 집합. {'a': 1, 'abc':5} 와 같이 표현.
<br><br>

*set*: 말 그대로 집합이다. dictionary와 같이 중괄호{} 를 사용하지만 key가 없고 값만 존재한다. 내부 원소는 불변한 값만 가질 수 있다(list 불가능)
<br><br>

*Booleans(bool)*: 논리값으로 True 와 False 만을 가짐

---

### 인덱싱과 슬라이싱(Indexing and Slicing)
<br>
**String형**은 순서가 있는 자료형이기에 인덱싱과 슬라이싱이 가능하다.
우리는 이를 이용해 문장에서 우리가 원하는 부분을 잘라서 가져올 수 있다.
<br>
![image](https://user-images.githubusercontent.com/52132160/91125956-e3aabd80-e6dd-11ea-8cde-1fe49f103b91.png)
> 인덱싱의 사용 예시
![image](https://user-images.githubusercontent.com/52132160/91126708-97f91380-e6df-11ea-8639-ea801a5f764a.png)


**슬라이싱**을 이용하면 문장의 일부문을 가져오는 것이 가능한데 [start:stop:step] 과 같은 규칙을 통해서 잘라낼 수 있다.
   - start 에는 잘라낼 부분의 시작 인덱스를 넣어준다.
   - stop 부분에는 마지막 인덱스를 넣을 수 있으나 **이 인덱스는 포함되지 않는다**.
   - step 은 건너뛸 규칙을 넣는 부분이다. 
<br><br>

**전체 출력, 역순 출력, step을 이용한 출력 예시**
![image](https://user-images.githubusercontent.com/52132160/91127392-1efabb80-e6e1-11ea-9f51-0625ba7ab45a.png)

---

### Formatting을 이용한 출력

![image](https://user-images.githubusercontent.com/52132160/91128283-e0fe9700-e6e2-11ea-9397-038886bf07d8.png)
파이썬으로 출력할 때 위와 같이 문자 + 변수 형식으로 붙여쓰는 경우가 많은데 
{}.format 형식을 사용하면 더 깔끔하게 출력이 가능하다. <br><br>
![image](https://user-images.githubusercontent.com/52132160/91128429-2ae77d00-e6e3-11ea-8e1f-14d43b1e9bfe.png)
<br><br>

> 이런 식으로 응용도 가능하다
![image](https://user-images.githubusercontent.com/52132160/91129129-69ca0280-e6e4-11ea-9af0-167499327073.png)
<br>

여담으로 fstring을 이용한 방법도 있는데 3.6 버전부터 가능하다. 본인의 기호에 맞게 사용하면 된다.
![image](https://user-images.githubusercontent.com/52132160/91129412-f70d5700-e6e4-11ea-95e3-c4c3602c951e.png)


---



