TOP
=======

+ 아무 옵션을 주지 않은 top을 입력하면 상단과 하단의 두 개의 영역으로 구분되어 내용이 표시됩니다. 상단에는 시스템에 대한 전반적인 요약 정보가, 하단에는 프로세스별 구체적인 정보가 표기됩니다. 정보는 3초마다 업데이트됩니다.




![top](https://github.com/cheoulsoo/cheoulsoo/assets/166576353/3b9e8c46-cb09-4e51-b9a2-d36b21547085)

-------------
*상단 정보*


+ **첫번째 줄**(top -)은 왼쪽부터 순서대로 현재 시간, 컴퓨터가 연속으로 실행되고 있는 시간, 로그인 한 사용자 수, 로드 에버리지(load average)를 보여줍니다. 로드 에버리지는 숫자가 3개인데, 차례로 1분, 5분, 15분 간의 로드의 평균을 나타냅니다.

+ **두번째 줄**(task)은 프로세스의 상태를 표시합니다. 순서대로 총 프로세스 수, 실행되고 있는 프로세스 수, 대기 중인 프로세스 수, 멈춘 프로세스 수, 좀비 상태인 프로세스 수를 의미합니다.

+ **세번째 줄**(Cpu)은 CPU 사용 정보를 나타냅니다. 아래 정보에 따라 각각 비율이 표기됩니다.
  + us : 사용자 영역 프로세스에서의 CPU 사용률입니다.
  + sy : 커널 영역 프로세스에서의 CPU 사용률입니다.
  + ni : 우선순위로 할당된 사용자 영역 프로세스를 실행하는데 소요되는 CPU 사용률입니다.
  + id : CPU를 사용하고 있지 않은 비율입니다.
  + wa : I/O가 완료될 때까지 기다리는 CPU 사용률입니다.
  + hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
  + si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
  + st : CPU를 가상 머신에서 사용함으로써 생기는 손실된 CPU의 비율
 
+ **네번째 줄**(Mem)은 물리 메모리 사용 정보를 나타냅니다. 그 뒤로는 순서대로 총 메모리(total), 여유 메모리(free), 사용 중인 메모리(used), 버퍼 또는 캐시 메모리(buff/cache)를 의미합니다.

+ **다섯번째 줄**(Swap)은 스왑 메모리 정보를 나타냅니다. 표기 방식은 물리 메모리와 동일합니다. 스왑 메모리는 가상 메모리로 불리며, 메모리가 부족할 때 디스크 공간을 이용해서 부족한 메모리 공간을 대체할 수 있는 메모리입니다. 때문에 물리 메모리가 가득 차도 스왑 메모리에 여유가 있으면 프로세스를 구동할 수 있습니다.

------
*하단 정보*


+ PID : 프로세스 ID입니다.
+ USER : 프로세스의 소유 계정입니다.
+ PR : 프로세스 우선순위입니다.
+ NI : PR에 영향을 주는 나이스 값입니다.
+ VIRT : 프로세스가 사용하고 있는 가상 메모리의 총량입니다.
+ RES : 프로세스가 사용하고 있는 물리 메모리의 양입니다.
+ SHR : 다른 프로세스와의 공유 메모리입니다.
+ S : 프로세스의 상태를 의미합니다. D는 네트워크 I/O를 대기하고 있는 상태, R은 실행 중인 상태, S는 대기 상태, Z는 좀비 상태입니다. 좀비 상태란 부모 프로세스가 죽은 자식 프로세스를 의미합니다.
+ %CPU : 프로세스의 CPU 사용률입니다.
+ %MEM : 프로세스의 물리 메모리 사용률입니다.
+ TIME+ : 100초 안에 사용하는 CPU 사용량입니다.
+ COMMAND : 명령줄입니다.

  **하단 정보는 키보드 방향키 위, 아래 키와 페이지 업, 다운 키로 목록을 이동할 수 있습니다.**

  -----------
  PS
  =====

+ ps 명령어 주요 옵션
 
    |옵션|설명|
    |---|---|
    |-e|시스템의 모든 프로세스를 표시합니다.|
    |-f|전체 형식으로 프로세스 정보를 표시합니다.|
    |-u 사용자명|지정된 사용자의 프로세스를 표시합니다.|
    |-p 프로세스ID|지정된 프로세스 ID의 프로세스를 표시합니다.|
    |-l|긴 형식으로 프로세스를 표시합니다.|
    |-a|터미널과 연관된 프로세스와 다른 사용자의 프로세스를 표시합니다.|
    |-x|터미널과 연관되지 않은 프로세스도 포함하여 표시합니다.|

+ ps 명령어 사용 예시

  
 `$ ps -ef`
 
  `$ ps -u user1`
  
  `$ ps -f | grep 프로세스명`
  
   `$ ps -ef | grep 프로세스명 `

+ 프로세스의 상태 코드 이해하기
  
    +   **R (Running)**: 프로세스가 실행 중이거나 실행을 위해 준비되어 있습니다.
    +   **S (Sleeping)**: 프로세스가 대기 상태에 있으며, 특정 이벤트나 조건이 발생할 때까지 활성화되지 않습니다.
    +   **T (Stopped)**: 프로세스가 중지되었거나 트레이스/디버그 중입니다.
    +   **Z (Zombie)**: 프로세스가 종료되었지만, 부모 프로세스에 의해 아직 회수되지 않은 상태입니다.
    +   **D (Uninterruptible Sleep)**: 프로세스가 디스크 입출력과 같은 시스템 활동에 의해 대기 상태에 있으며, 인터럽트할 수 없는 상태입니다.
 
-------------
JOBS
=====

+ 사용 방법
     + __-l__ : 프로세스 그룹 ID를 state 필드 앞에 출력한다.
     + __-n__ : 프로세스 그룹 중에 대표 프로세스 ID를 출력한다.
     + __-p__ : 각 프로세스 ID에 대해 한 행씩 출력한다.
     + __command__ : 지정한 명령어를 실행한다.


```
jobs[옵션][jobID]

jobs -x command[args]

```


+ 설명 및 예제
  +현재 환경의 작업 상태를 아래와 같이 확인할 수 있다.

```
$ jobs
[1]- 정지됨                     vi
[2]+ 정지됨                     tail -f /var/log/messages
```

  + -l 옵션은 state 필드 앞에 프로세스 ID를 출력한다.

```
$ job
[1]- 4908Stopped  (tty output)               vi
[2]+ 4987Stopped                             tail -f /var/log/messages
```

+ jobs 명령어로 확인할 수 있는 세션의 상태값은 다음과 같다.

    |옵션|설명|
    |---|---|
    |Running|시스템의 모든 프로세스를 표시합니다.|
    |Done|전체 형식으로 프로세스 정보를 표시합니다.|
    |Done (code)|지정된 사용자의 프로세스를 표시합니다.|
    |Stopped|지정된 프로세스 ID의 프로세스를 표시합니다.|
    |Stopped (SIGTSTP)|긴 형식으로 프로세스를 표시합니다.|
    |Stopped (SIGSTOP)|터미널과 연관된 프로세스와 다른 사용자의 프로세스를 표시합니다.|
    |Stopped (SIGTTIN)|터미널과 연관되지 않은 프로세스도 포함하여 표시합니다.|
    |Stopped (SIGTTOU)|터미널과 연관되지 않은 프로세스도 포함하여 표시합니다.|

------------------
KILL
======

+ 사용 방법
     + __pid ···__ : 종료시킬 프로세스 ID나 프로세스 이름을 지정한다.
     + __-s__ : 전달할 시그널의 종류를 지정한다. 여기에는 시그널 이름이나 번호를 써준다.
     + __-l__ : 시그널로 사용할 수 있는 시그널 이름들을 보여준다. 이은/usr/include/linux/signal.h 파일에서도 알 수 있다.
     + __-1,__ : -HUP 프로세스를 재활성화한다.
     + __-9__ : 프로세스를 강제로 종료시킨다.


```
kill [시그널][-a]pid...

kill-l [시그널]

```

+ 설명 및 예제

    *kill 명령어는 프로세스에 종료 시그널을 보낸다. 시스템에 얘기치 않은 문제가 생긴 프로세스를 종료시킬 수 있다. 만일 kill 명령으로 종료되지 않는 프로세스는 -9 옵션을 사용해서 강제로 종료하면 된다.*

  +아래와 같이 ps 명령어로 sshd 프로세스를 확인할 수 있다.

  ```
  # ps aux | grep sshd
  root           2518 0.0 0.1 7084 1076 ?     Ss  Jun07 0:00 /usr/sbin/sshd
  root           12095 0.0 0.3 9936 2812 ?    Ss  02:34 0:00 /usr/sbin/sshd
  root           12097 0.0 0.2 9936 1604 ?    S   02:34 0:00 /usr/sbin/sshd
  root           12216 0.0 0.0 3932 684 pts/1 R+  02:46 0:00 /usr/sbin/sshd
  ```

+ 현재 sshd 프로세스는 root 사용자 권한으로 동작하고 있으며 PID는 2518와 12095이다. 참고로 ps aux 명령에서 볼 수 있는 프로세스 정보에 대한 각각의 필드 내용은 다음과 같다.

|Root|USER|프로세스의 사용자|
|---|---|---|
|2518|PID|프로세스 ID|
|0.0|%CPU|마지막 1분 동안 프로세스가 사용한 CPU 점유율|
|0.1|%MEM|마지막 1분 동안 프로세스가 사용한 메모리의 점유율|
|7084|VSZ|가상메모리에 있는 프로세스의 KB 단위 크기|
|1076|RSS|프로세스의 실제 메모리의 크기로 KB 단위|
|?|TTY|연결되어 있는 터미널|
|Ss|STAT|실행되고 있는 프로세스 상태|
|Jun07|START|프로세스가 시작된 날짜
|0:00|TIME|프로세스가 소비한 총 시간
|/usr/sbin/sshd|COMMAND|사용자가 실행한 명령 이름|

+ ps 명령으로 확인한 PID를 이용하면 원하는 프로세스를 종료시킬 수 있다.
  
`#kill 2518`

+ 만일 kill 명령으로 종료되지 않으면 -9 옵션으로 강제 종료해보자.
  
`#kill -9 2518`

+ kill -HUP pid 명령을 이용하면 프로세스를 종료 후 다시 재실행한다.
  
`#kill -HUP 2518`

-----------





     


     
     
  
    





    
