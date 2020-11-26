---
layout: post
title:  "파이썬에서 자주 혼동되는 내용 정리(4) - 파일 입출력"
author: Peter
categories: [ Python ]
image: https://user-images.githubusercontent.com/52132160/91701223-ef9cf080-ebb1-11ea-88c2-7983ceabbb5a.png

sitemap:
changefreq: daily
priority: 1.0
---
---

### 파일 입출력(I/O)


**%%writefile 로 txt 파일 쓰기** 
![image](https://user-images.githubusercontent.com/52132160/91330985-25825380-e805-11ea-96ed-46f1322005a9.png)
<br><br>

**pwd로 경로 확인**
![image](https://user-images.githubusercontent.com/52132160/91331169-637f7780-e805-11ea-9566-344883999a51.png)
여기 나타난 경로에 내 txt 파일이 저장된다.
<br><br>

**파일 열기 및 읽어오기**
![image](https://user-images.githubusercontent.com/52132160/91331243-7db95580-e805-11ea-9327-e19fe9e18fe4.png)
\n은 개행 표시이다.(모든 문장을 하나의 string 으로 가져옴)
<br><br>

**파일 포인터 초기화**
![image](https://user-images.githubusercontent.com/52132160/91331363-a3465f00-e805-11ea-95ad-7b72dadf37e4.png)
다시 한번 파일을 읽어오려 하면 '' 이 출력되는데, 파일 포인터가 이미 텍스트를 모두 읽고 더 이상 뒤에 아무것도 없기 때문이다. 당황하지 말고 seek을 사용하여 파일 포인터를 앞으로 땡겨주면 된다.  
<br><br>

**readline()**
![image](https://user-images.githubusercontent.com/52132160/91331867-53b46300-e806-11ea-8333-dcb2f3f2e2ac.png)
기존에 read는 모든 문장을 하나로 받았다면 readline은 각 문장마다(\n 단위) 끊어서 저장되어 반복문을 사용할 수 있게 된다. 
<br><br>

---

### 다른 경로에 저장된 파일 입출력

![image](https://user-images.githubusercontent.com/52132160/91431077-cff88600-e89a-11ea-85e2-c088ad539b86.png)
open 안에 모든 경로를 입력시켜주면 된다.
<br><br>

![image](https://user-images.githubusercontent.com/52132160/91431530-75abf500-e89b-11ea-80da-49c553ca9541.png)
다 사용한 파일은 close 를 사용하여 닫아주어야 한다! 하지만 우리는 좀 더 편한 방법을 사용할 수 있는데, 
![image](https://user-images.githubusercontent.com/52132160/91432017-1b5f6400-e89c-11ea-9c06-2d83c418a9c4.png)
이런 식으로 선언해 주면 indent 안에서만 돌아가기 때문에 close를 안써도 된다.
<br><br>
**읽기 모드를 이용한 예시**
![image](https://user-images.githubusercontent.com/52132160/91432623-f6b7bc00-e89c-11ea-9ef8-a6b27701edcb.png)
read()는 전체 문장 출력, readline()은 첫문장만 출력
<br><br>

**쓰기 모드**
![image](https://user-images.githubusercontent.com/52132160/91433418-36cb6e80-e89e-11ea-8ed0-bd4c8d0d3381.png)
mode = 'w'를 사용하면 기존에 입력되었던 문장 뒤에 쓰여지는 것이 아니라 그냥 덮어쓰게 되고 기존 내용은 모두 사라진다.
이를 방지하기 위해서는 'a' 를 사용하면 되는데 다음을 참고하면 된다.
<br><br>

**파일 입출력 append 기능**
![image](https://user-images.githubusercontent.com/52132160/91432854-4e562780-e89d-11ea-971a-fb091f3a83cf.png)
mode = 'a' 를 사용하면 write처럼 덮어쓰지 않고 list의 append처럼 뒤로 붙여 쓸 수 있다.
<br><br>

---
