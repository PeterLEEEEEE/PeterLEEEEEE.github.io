---
layout: post
title: "Flask 시작하기(1) - 가상환경"
author: Peter
categories: [python]
image: https://user-images.githubusercontent.com/52132160/100248630-0ec3d800-2f7f-11eb-9cc3-db0f10ae26eb.png

tags: [Flask]
sitemap:
changefreq: daily
priority: 1.0
comments: true
use_math: true
---

---

### 명령프롬프트(cmd)에서 실행

---

mkdir로 디렉토리 하나 만들기
<br><br>
python -m venv myproject 입력 (myproject는 폴더명이니 알아서 선택)
<br><br>
start . 은 해당 폴더 여는 기능

cd myproject 후
Scripts\activate 입력하면 된다.

---

### Flask 설치

가상환경에 들어오게 되면 앞에 () 표시가 되면 잘 된 것이다.

pip install flask로 플라스크를 설치하자

---

### Anaconda 환경에서 만드는 법

anaconda prompt 실행

conda create -n my_flask flask
하면 가상환경이 생기면서 flask도 같이 깔린다.

activate my_flask 하면 가상환경 진입 성공

- conda list 입력하면 설치된 패키지 목록을 볼 수 있음

---

---
