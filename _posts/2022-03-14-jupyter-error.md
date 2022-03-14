---
layout: single
title: "[Error] Bad file descriptor"
categories:
    - Others
---

<br>

**Anaconda Jupyter 실행 시 오류**

Jupyter notebook 실행 시 anaconda prompt :

Bad file descriptor (cpp:100) 이라는 오류가 나타났다.

이때 해결 방법은 , 기존에 사용 중인 Anaconda prompt를 실행한 후

<br>

```
pip uninstall pyzmq

pip install pyzmq==19.0.2
```

<br>

를 차례로 입력해주면 손쉽게 해결된다.