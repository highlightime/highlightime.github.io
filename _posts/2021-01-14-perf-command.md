---
title: Performance Counter for Linux
categories: Perf
published: true
---

- 리눅스 성능 분석을 위한 툴
- 함수/소스라인 단위
- 이벤트 샘플링을 통해 특정 프로그램 / 시스템 전반 분석
- 성능 측정가능한 초점 : CPU cycles, cache-misses, page-fault, system calls, etc

장점 : 각종 event 중에서 system layer 상 원하는 성능분석 지점 focus 선택가능



### kernel 의 주요 5가지 subsystem

1. process 
2. memory
3. device driver
4. file system
5. networking



### perf 의 사용 목적

1. Profiling : 병목지점을 찾아내기 위해 - 어떤 함수/소스라인이 CPU 많이 사용하는지
2. Tracing : 특정 event 발생에 대한 경위, 과정을 살펴보기 위해



### perf stat

command 실행 결과를 쉘에 바로 출력

```
sudo ./perf stat <options> <command>
```

주요 옵션
e <event>: 측정할 이벤트들을 지정

p <pid>: 이벤트를 측정할 프로세스의 pid를 지정 

C <cpu>: 이벤트를 측정할 cpu를 지정



### perf list

performance 측정 가능한 event list 확인



### perf record

측정 결과를 perf.data에 기록

perf report로 결과 확인 가능

주요 옵션
 e <event>: 측정할 이벤트들을 지정
 p <pid>: 이벤트를 측정할 프로세스의 pid 설정 C <cpu>: 이벤트를 측정할 cpu를 설정
 F <freq>*:* 샘플을 생성할 frequency 설정



> 1. 실행되지 않고 있는 프로세스 측정
>
>    ```
>     sudo ./perf record -e <event> <command> 
>     //e.g)  ./perf record -e cs ls (ls 명령을 쉘에서 수행했을 때, context switch 발생 횟수를 카운팅해라)
>     sudo ./perf report ==> 위에서 얻어진 perf.data 파일을 읽어서 결과를 출력해줌.
>    ```
>
>    
>
> 2. 실행 중인 프로세스 측정
>
>    ```
>      sudo ./perf record -p <pid> -e <event>  
>      // e.g) ./perf record -p 19189 -e cs (19189 프로세스의 context switch 발생 횟수 기록한다. perf 프로세스 종료시키면, 검사도 종료된다)
>      sudo ./perf report
>    ```





### perf mem

load/store 명령어 사용 횟수 측정

> ```
> sudo ./perf mem record <record 옵션과 동일>  
> // e.g) sudo ./perf mem record ls (ls 명령 쉘에서 실행했을 때, load/store 명령의 실행 횟수를 구하라)
> sudo ./perf mem report 
> // 위 측정 결과 확인
> ```



성능이 중요한 바이너리에 대해 최적화 확인 용도로 활용 가능 

같은 기능에 더 적은 memory operations 이면 성능 좋다.



### perf kmem

kernel memory 가 몇 번 할당/해제되었는지 측정

> 1. 
>
> ```
>  sudo ./perf kmem record ls  ==> perf mem 과 사용방법 완전히 같다. 
>  sudo ./perf report  ==> 위 측정 결과 확인
> ```
>
>  
>
> 2. 커널 부팅부터 현재까지 slb allocator 의 동작에 대해 출력 
>
> ```
> sudo ./perf kmem stat
> ```
>
> 



### perf top

real-time 성능 측정 결과 출력

```
sudo ./perf top
```

























