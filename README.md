# Linux Commands 
**-top, ps, jos, kill-**


### top 명령어
---------
top : 시스템의 CPU, 메모리 사용량, 실행 중인 프로세스 목록을 실시간으로 갱신하며 보여준다.

**top명령어의 실행법**

`$ top`

<img width="1537" height="365" alt="image" src="https://github.com/user-attachments/assets/34295839-f51b-4737-ab98-ec083f5034e4" />


*top 명령어의 실행 사진*

실행결과는 크게 두 부분으로 나뉜다. 

**Upstream (상단 요약 영역)**: 시스템 전체의 CPU, 메모리, 부하량 정보를 나타낸다.

**Task Area (하단 프로세스 영역)**: 개별 프로세스들의 상세 정보 리스트를 나타낸다.

-----

**첫 번째 줄** : 시스템 시간 및 부하를 나타낸다.

* 이 때 주요하게 봐야할것은 load average이다. 

* 이는 시스템 부하량의 지표인데 순서대로 1분, 5분, 15분 평균 부하량이다.
써져있는 숫자가 CPU코어 수 보다 낮으면 여유, 높으면 과부하 상태이다.

**두 번째 줄** : 프로세스의 상태를 요약하여 보여준다.

* running은 현재 실제로 CPU를 쓰고있는 프로세스 수를 나타낸다.

* zombie는 종료 되었으나 부모 프로세스가 아직 회수하지 않은 '좀비' 상태. 이 숫자가 계속 늘어나면 프로그램 버그를 의심해야한다. 

**세 번째 줄** : CPU의 상세 사용율을 나타낸다.

* us : 사용자가 만든 프로그램이 사용하는 비율

* sy : 리눅스 커널이 사용하는 비율

* id : 아무 일도 안하고 노는 비율

* wa : CPU는 빠른데 디스크나 네트워크가 느려서 CPU가 기다리는 시간

**네번째, 다섯번째 줄** : 메모리의 정보를 나타낸다.

* total : 전체 물리 메모리 양

* used : 사용 중인 메모리

* buff/cache : 빌려 쓴 메모리의 양

* avail Mem : 실제로 새로운 프로세스가 사용할 수 있는 실질적 여유 메모리

----

**하단 프로세스 영역**

| 컬럼명 | 의미 | 상세 설명|
|-------|-------|---------|
|PID    | Process ID| 프로세스의 고유 번호|
|USER|User|누가 이 프로세스를 실행했는지|
|PR|Priority|실행 우선순위|
|NI|Nice value|우선순위 조절 값(낮을수록 우선순위가 높다)|
|VIRT|Virtual Memory|프로세스가 메모리를 예약한 양|
|RES|Resident Memory|프로세스가 실제로 사용하고 있는 RAM의 양|
|SHR|Shared Memory|다른 프로세스와 공유하는 메모리 양|
|S|Status|상태 (R:실행중, S:잠자는중, Z:좀비, D:디스크대기)|
|%CPU|CPU Usage|CPU 사용 퍼센트|
|%MEM|Mem Usage|물리 메모리 사용 퍼센트|
|TIME+|CPU Time|프로세스가 시작된 후 지금까지 CPU를 사용한 누적 시간|
|COMMAND|Command|실행된 명령어의 이름|



----------
### ps 명령어
------
특정시점의 시스템에서 실행 중인 프로세스 목록을 스냅샷(Snapshot) 형태로 보여주는 명령어

**ps명령어 사용법**

`$ ps [option]`

**ps명령어의 스타일**

|스타일|명령어|설명|출력 내용|
|------|-----|----|----|
|System V|`$ ps -ef`|-e (모든 프로세스), -f (풀 포맷)의 조합으로, 프로세스의 부모/자식 관계까지 포함된 자세한 정보를 출력|UID, PID, PPID, C, STIME, TTY, TIME, CMD|
|BSD|`$ ps aux`|모든 사용자의 (a), 터미널이 없는 (x), 자세한 정보 (u)를 출력|USER, PID, %CPU, %MEM, VSZ, RSS, TTY, STAT, START, TIME, COMMAND|

**ps와 top의 차이점**

* ps는 명령 실향 순간의 정보를 보여주지만 top는 실시간으로 갱신하여 정보를 보여준다.

* ps는 명령 실행 후 즉시 종료 하지만 top는 q를 누르기 전까지 실행 상태를 유지한다.

<img width="568" height="154" alt="image" src="https://github.com/user-attachments/assets/638750a6-f58a-4faa-a22d-283c03e7c07e" />

*옵션이 없는 ps실행사진*

<img width="1121" height="150" alt="image" src="https://github.com/user-attachments/assets/3f68a019-dd5b-4cfd-87b8-54846e4b1465" /> 

*-ef옵션 ps실행사진*

<img width="1478" height="155" alt="image" src="https://github.com/user-attachments/assets/2c769736-448d-44d1-af80-bbea82f154b8" />

*aux옵션 ps실행사진*


-----












