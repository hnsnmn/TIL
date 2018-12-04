# 운영 체에의 역할

## 시스템 자원 관리자
* Operating System 또는 OS 라고 부릅니다.
* 시스템 자원(System Resource) = 컴퓨터 하드웨어
    * CPU(중앙처리장치), Memory(DRAM, RAM)
    * I/O Devices (입출력 장치)
        * Moinitor, Mouse, Keyboard, Network
    * 저장 매체 : SSD, HDD (하드디스크)

> 컴퓨터 하드웨어는 스스로 할 수 있는 것이 없습니다.

1. CPUL: 각 프로그램이 얼마나 CPU를 사용할지를 CPU가 결정 할 수 없습니다.
2. Memory: 각 프로그램어 어느주소에 저장더ㅣ어애 하는지, 어느 정도 메모리 공간을 확보해줘야 하는지를 결정 할 수 없습니다.
3. 저장매체(HDD, SDD): 어떻게, 어디에 저장할지 결정할 수 없습니다.
4. 키보드/마우스 : 스스로 표시 할 수 없습니다

> 이 모든 것들을 운영체제가 진행합니다.

## 사용자와 컴튜간의 커뮤니케이션 지원


## 응용 프로그램 이란?
* 프로그램 = 소프트웨어
* 소프트웨어 = 운영체제, 응용 프로그램

# 시분활 시스템 멀티 태스킹
* 응용 프로그램이 CPU를 사용하는 시간을 잘개 쪼개서, 여러 개의 응용 프로그램이 동시에 실행사는 기법
* 시분할 시스템 : 다중 사용자를 지원하고, 컴퓨터 응답 시간을 최소하하는 시스템
* 멀티 태스킹 
    * 가능한 CPU를 많이 활용하도록 하는 기능(시간대비 CPU사용율을 높이자)
    * 단일 CPU에서, 여러 응용 프로그램의 병렬 실행을 가능케 하는 시스템 
* 멀티 프로그래밍 : 최대한 CPU를 많이 활용 하도록 하는 시스템(시간대비, CPU 활용도를 높이자)
    * I/O 작업이 일어나면 CPU가 대기 상태로 넘어가는 것을 비동기 방식으로 CPU를 다른 작업을 진행 할 수 있게 진행

# CPU Protection Rings
* CPU도 권한 모드라는 것을 가지고 있습니다.
    * 사용자 모드
    * 커널 모드 : 특권 명령어 실행과 원하는 작업 수행을 위한 자원 접근을 가능케 하는 모드

## 시스템콜은 커널 모드로 실행
* 커널 모드에서만 실행 가능한 기능들이 있음
* 커널 모드로 실행 하려면, 반드시 시스템 콜(커널모드)을 해야함
* 시스템 콜은 운영체제 제공

## 사용자 모드와 커널 모드
* 함부로 응용 프로그램이 전체 컴퓨터 시스템을 헤치지 못함
* 운영체제는 시스템 콜을 제공
* 프로그래밍 언어 별로 운영체제 기능을 활요하기 위해, 시스템 콜을 기반으로 API 제공
* 응용 프로그램은 운영체제 기능 필요시, 해당 API를 사용해서 프로그램을 작성
* 응용 프로그램이 실행되서, 운영체제 기능이 필요한 API를 호출하면, 시스템 콜이 호출되서, 다시 커널 모드 변경되어 OS 내부에 해당 명령이 실행되고, 다시 응용 프로그램으로 돌아간다.

# 멀티 프로그래밍
* 최대한 CPU를 많이 활용하도록 하는 시스템
    * 시간 대비 CPU 활용도를 높이자
    * 으용 프로그램 짧은 시간안에 실행 완료를 시킬 수 있음
## 멀티 프로그래밍
* 응용 프로그램은 온전히 CPU를 쓰기보다, 다른 작업을 중간에 필요로 하는 경우가 많음
    * 응용 프로그램이 실행되다가 파일을 읽는다.
        * I/O 작업이 일어나면 시스템이 Blocking 된다
    * 응용 프로그램이 실행되다가 프린팅을 한다.
        * 마찬 가지로 I/O 작업이 일어나면 Blocking 된다
## 정리
* 시분할 시스템 : **다중 사용자 지원**, 컴퓨터 응답시간을 최소화 하는 시스템
* 멀티 캐스팅: **단일 CPU에**서 여러 응용 프로그램을 동시에 실행하는 것처럼 보이게 하는 시스템
* 멀티 프로세싱 : **여러 CPU**에 하나의 응용 프로그램을 병렬로 실행하게 해서, 실행속도를 높이는 기법
* 멀티 프로그래밍 : 최대한 CPU를 일정 시간당 많이 활용하는 시스템


# 스케줄러 알고리즘
## 프로세스란 ?
* 실행 중인 프로그램은 프로세스라고 함
    * 프로세스 : 메모리에 올려져서, 실행 중인 프로그램
    * 코드 이미지(바이너리): 실행 파일, 예

## 스케줄러와 프로세스
* 프로세스 실행을 관리하는 것이 스케줄러

## 스케쥴링 알고리즘
* 목표
    * 시분할 시스템 예: 프로세스 응답 시간을 가능한 짧게
    * 멀티 프로그래밍 예: CPU 활용도를 최대로 높혀서, 프로세스를 빨리 실행

## 최단 작업 우선(SJF) 스케줄러
* SJF 스케줄러 
    * 가장 프로세스 실행 시간이 짧은 프로세스 부터 먼저 실행 시키는 알고리즘

## 우선순위 기반 스케쥴러
* priority-based 스케줄러
    * 정적 우선순위
    * 프로세스마다 우선순위를 미리 지정
    * 동적 우선순위 : 스케줄러가 상황에 따라 우선순위를 동적으로 변경 

## Round Robin 스케줄러
* 큐에 쌓아 놓고 일정 시간이 지나면 다시 대기 큐로 돌려 보낸다. 그 뒤에 있는 작업을 진행한다.

## 정리
* FIFO 스케줄링 알고리즘 : 배치 시스템
* 최단 작업 우선 스케줄링 알고리즘
* 우선순위 기반 스케줄링 알고리즘
    * 정적 순위, 동적 우선 순위
* Round Robin 스케줄링 알고리즘
    * 시분할 시스템 기반

  
## 프로세스 상태

![](/assets/process-flow.png)
* running state: 현재 CPU에서 실행 상태
* ready state: CPU에서 실행 가능 상태 (실행 대기 상태)
* block state: 특정 이벤트 발생 대기 상태

## 프로세스 상태간 관계

![](/assets/proccess-status.png)

1. Process blocks for input : 특정 이벤트 대기
2. Scheduler picks another process
3. Scheduler picks this process
4. Process Becomes avaliable

## 입터럽트
 
> CPU가 프로그램을 실행하고 있을때, 입출력 하드웨어 등 의 장치(이벤트 발생)나 또는 예외상횡이 발생하여 처리가 필요한 경우 CPU에 알려준 처리 기술

> 어느 한순간 CPU가 실행하는 명령은 단 하나, 다른 장치와 어떻게 커뮤니케이션을 할까요?

### 입터럽트 필요 이유

* 선점형 알고리즘
    * 프로그램이 실행중에 어떠한 이유(Blocking 되는 작업 등)로 중간에 멈춰야 할때 
* 예외 상황 핸들링
    * CPU가 프로그램을 실행하고 있을 때, 입출력 하드웨어 등의 장치나 또는 예외상황이 발생할 경우, CPU가 해당 처리를 할 수 있도록 CPU에 알려줘야함