# Open Source SW
리눅스 명령어 top, ps, jobs, kill 명령어에 대해서 알아보자.

**top**
---
시스템 프로세스/메모리 사용현황을 실시간으로 출력하는 명령어
![image](https://github.com/thddbswl/opensourceSW/assets/115966686/deb4c41f-f3cc-42b8-863c-96aad39f8466)

top - 시스템 현재 시간, OS가 구동된 시간, 접속 중인 유저 수 출력

load average:  왼쪽부터 각각 1분, 5분, 10분 동안의 평균 시스템 부하를 출력

tasks: 현재 프로세스 상태에 대해 출력

%Cpu(s): CPU의 사용율을 출력
- us: 유저 영역
- sy: 커널 영역
- ni: 프로세스 우선순위 설정에 사용되는 Cpu사용율
- id:사용하지 않는 Cpu 비율
- wa: I/O 대기 상태의 CPU 사용율
- hi: 하드웨어 인터럽트에 사용되는 Cpu 사용율
- si: 소프트웨어 인터럽트에 사용되는 CPU  사용율
- st: Hypervisor VM에서 사용하여 대기하는 CPU 비율

MiB Mem: RAM의 정보 출력, MiB Swap: Swap의 메모리 영역 출력 (total: 총 메모리 양, free: 사용 가능 메모리 양, used: 사용 중인 메모리 양, buff/cache: I/O에 사용되는 버퍼 메모리 양)

PID: 프로세스 ID

USER: 프로세스를 시작한 유효한 사용자의  ID

PR: 작업의 우선순위

NI: 우선순위에 영향을 주는 값 (음수는 우선순위가 높고 양수는 낮음)

VIRT: 가상메모리 크기

RES: 상주메모리 크기

SHR: 공유메모리

S: 프로세스의 상태
- R: Runnung
- S: Sleeping
- I: Idle
- D: Uninterruptable Sleep
- T: 작업 제어 신호에 의해 중지됨
- t: Trace 중 디버거에 의해 중지됨
- Z: Zombie

%CPU : CPU 사용량

%MEM : 메모리 사용량

TIME+ : 프로세스가 사용한 CPU 시간

COMMAND : 명령어 이름

---
**top 명령어를 실행 한 뒤**

TOP 나가기: q

k: 특정 프로세스 종료
>k를 입력하고 PID를 입력하면 signal을 입력 후  9(sigkill) 시그널 혹은 15(sigterm) 시그널을 주어 프로세스를 종료할 수 있다.
>

정렬하기
P: CPU 사용량으로 정렬, M: 메모리 사용량으로 정렬, N: PID 순으로 정렬, T: Running Time으로 정렬, R: 오름차순과 내림차순 토글 변경

H: 쓰레드 기준으로 출력

-스페이스 바: 즉시 업데이트

---

출처

{https://code-lab1.tistory.com/332} ([Linux] 리눅스 top 명령어 사용법, 리눅스 CPU 및 메모리 체크하는 법, 코드 연구소:티스토리)
