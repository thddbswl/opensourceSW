# Open Source SW
리눅스 명령어 top, ps, jobs, kill 명령어에 대해서 알아보자.

*top*
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
**명령어 출력 항목**

TOP 나가기: q

>*시그널
>- 1(SIGHUP): 터미널에서 접속이 끊겼을 때 보내지고, 변화된 내용 적용을 위해 재시작할 때 사용
>- 2(SIGINT): Ctrl+c 입력시 보내지고, 인터럽트 시그널로 실행을 중지
>- 3(SIGQUIT): 실행 중지 시그널, Ctrl+\ 입력시 보내짐
>- 9(SIGKILL): 프로세스 강제 종료
>- 15(SIGTERM): kill의 기본 시그널, 정상 종료시킴
>- 18(SIGCONT): 시그널에 의해 정지된 프로세스 다시 실행
>- 19(SIGSTOP): 정지 시그널
>- 20(SIGTSTP):일시정지 시그널, Ctrl+z 입력 보내짐

k: 특정 프로세스 종료(kill)
>k를 입력하고 PID를 입력하면 signal을 입력 후  9(sigkill) 시그널 혹은 15(sigterm) 시그널을 주어 프로세스를 종료할 수 있다.

killall: 여러 프로세스 종료
>- -l: 시그널 종류 출력
>- -s: 시그널 이름 지정
>- -v: 시그널 전송 결과 출력
>- -w: 시그널 받은 프로세스가 종료될 떼까지 대기

pkill: 프로세스 이름과 지정한 패턴이 부합하는 프로세스 종료

정렬하기
P: CPU 사용량으로 정렬, M: 메모리 사용량으로 정렬, N: PID 순으로 정렬, T: Running Time으로 정렬, R: 오름차순과 내림차순 토글 변경

H: 쓰레드 기준으로 출력

-스페이스 바: 즉시 업데이트

*ps*
---
현재 실행 중인 프로세스와 상태를 출력하는 명령

[Linux] 리눅스 top 명령어 사용법

>- USER(BSD): 프로세스 소유자의 이름
>- UID(System V): 프로세스 소유자의 이름
>- PID: 프로세스 식별번호
>- PPID: 부모 프로세스의 PID
>- %CPU: CPU 사용 비율의 추정치(BSD)
>- %MEM: Memory 사용 비율의 추정치(BSD)
>- VSZ: K 단위 또는 페이지 단위의 가상 메모리 사용량
>- RSS: 실제 메모리 사용량
>- TTY: 프로세스와 연결된 터미널
>- S(System V): 현재 프로세스의 상태 코드
>- STAY(BSD): 현재 프로세스의 상태 코드
>- TIME: 총 CPU 사용 시간
>- COMMAND: 프로세스의 실행 명령행
>- STIME: 프로세스가 시작된 시간 또는 날짜
>- C(System V): 짧은 기간 동안의 CPU 사용률
>- CP(BSD): 짧은 기간 동안의 CPU 사용률
>- F: 플래그
>- PRA: 실제 실행 우선순위
>- NI: nice 우선순위 번호

**명령어 옵션**

>- -A: 모든 프로세스를 출력
>- a:(BSD): 터미널과 연관된 프로세스를 출력, x 옵션과 같이 사용하여 모든 프로세스를 출력할 때 사용
>- -a: 세션 리더를 제외 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력
>- -e: 커널 프로세스를 제외 모든 프로세스를 출력
>- -f: 출력을 풀 포맷으로 표기, UID, PID , PPID 등이 함께 표시
>- -l(System V): 출력을 긴 포맷으로 표기, 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI 값과 NI 값을 확인
>- l(BSD): 출력을 긴 포맷으로 표기, 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI 값과 NI 값을 확인
>- -o: 출력 포맷을 지정
>- -M: 64비트 프로세스들 출력
>- -m: 프로세스와 커널 스레드 출력
>- -p: 특정 PID를 지정하여 출력
>- -r: 현재 실행 중인 프로세스 출력
>- u(BSD): 프로세스의 소유자 기준으로 출력
>- -u[사용자]:특정 사용자의 프로세스 정보를 출력, 사용자를 지정하지 않는다면 현재 사용자 기준으로 출력
>- x(BSD): 터미널에 종속되지 않은 프로세스 출력
>- -x: 로그인 상태에 있는 동안 아직 완료되지 않은 프로세스 출력

*jobs*
---
작업의 상태 표시하는 명령어

'''c
jobs [옵션] [작업번호]
'''

**명령어 출력 상태**

>Running: 작업 진행 중
>Done: 작업이 완료되어 0을 반환
>Done(code): 작업이 종료되고 0이 아닌 코드를 반환
>Stopped: 작업 일시 중단
>Stopped(SIGTSTP): SIGTSTP 시그널이 작업 일시 중단
>Stopped(SIGSTOP): SIGSTOP 시그널이 작업 일시 중단
>Stopped(SIGTTIN): SIGTTIN 시그널이 작업 일시 중단
>Stopped(SIGTTOU): SIGTTOU 시그널이 작업 일시 중단

**명령어 옵션**

-l: 프로세스 그룹 ID를 stste 앞에 출력

-n: 프로세스 그룹 중 대표 프로세스 ID를 출력

-p: 각 프로세스 ID에 대해 한 행씩 출력

-command:지정한 명령어 실핼

*kill*
---
프로세스  종료

1. ps 명령어로 PID를 얻고 kill명령어로 프로세스 종료
`
kill [PID]
`
2. 사용자 지정 시그널 전송 방법으로 종료
`
kill -s [signal] [PID]
`
-l 옵션을 이용해서 사용 가능한 시그널 목록을 볼 수 있다. 이때 15 시그널에 응답하지 않으면 9를 이용해 강제 종료할 수 있다.

>-l: 시그널 목록 표시
>-s: 지정한 시그널 보내기
>-9: SIGKILL 시그널을 보내 강제 종료
>-15: SIGTERM 시그널을 내 종료

---

출처

[https://code-lab1.tistory.com/332] ([Linux] 리눅스 top 명령어 사용법, 리눅스 CPU 및 메모리 체크하는 법, 코드 연구소:티스토리)

[https://blog.naver.com/PostView.nhn?blogId=tmk0429&logNo=222318530824] (ps 명령어 및 옵션 - 리눅스 프로세스 관리 [Linux 명령어]|작성자 tmk0429)

[https://sisiblog.tistory.com/209] ([Linux] 리눅스 kill 명령어 사용법(프로세스 죽이기), 달삼쓰뱉:티스토리)

[https://hbase.tistory.com/265] ([Linux] 리눅스 jobs 명령어 사용법, A6K 개발노트:티스토리)
