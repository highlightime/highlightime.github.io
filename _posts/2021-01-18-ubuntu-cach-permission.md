---
title: /proc/sys/vm/drop_caches permission denied
tags: Ubuntu, Cach
categories: Ubuntu
---

### 문제점

 커널 설정을 바꿀 때 sudo 를 붙여 실행해도 권한 문제가 발생한다.



### 이유

echo 명령에는 sudo를 적용하지만,
redirection후에는 원래 사용자 권한을 그대로 남겨두기 때문이다.



### 해결 1

```c
$ sudo sh -c "echo 3 > /proc/sys/vm/drop_caches"
```



### 해결 2

```c
$ sudo -s
```



### 해결 3

```c
$ echo 1 | sudo tee /proc/sys/vm/drop_caches
```

tee 명령 

- 기본적으로 stdin을 stdout으로 그대로 보내주는 역할
- 추가적으로 파일 이름이 argument로 주어지면 해당 파일에도 stdin의 내용을 쓴다.

