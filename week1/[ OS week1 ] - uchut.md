# CH 1. Introduction to Operating Systems

### 운영체제란?

운영체제는 컴퓨터 HW 바로 위에 설치되는 SW로서<br>
USER 및 다른 모든 SW와 HW를 연결하는 SW 계층

![OS](https://upload.wikimedia.org/wikipedia/commons/3/3a/Operating_system_placement_kor.svg)

**운영 체제의 목표**

1. 사용자가 컴퓨터 시스템을 편리하게 사용할 수 있는 환경 제공
   - 동시 사용자 / 프로그램들이 각각 독자적 컴퓨터에서 수행되는 것 같은 환경 제공
   - 하드웨어를 직접 다루는 복잡한 부분을 운영체제가 수행
2. 컴퓨터 시스템의 자원을 효율적으로 관리 (자원관리자)
   - processor, memory, i/o divice 등의 효율적 관리
      * 사용자간의 형평성 있는 자원 분배
      * 주어진 자원으로 최대한의 성능 추진
   - 사용자 및 운영체제 자신의 보호
   - process, file, message 등을 관리

**운영 체제의 분류**

1. 동시 작업 가능 여부
   - 단일 작업(single tasking)
      * 한 번에 하나의 작업만 처리
   - 다중 작업(multi tasking)
      * 동시에 두 개 이상의 작업 처리
2. 사용자의 수
   - 단일 사용자(single user)
   - 다중 사용자(multi user)
3. 처리 방식
   - 일괄 처리(batch processing)
      * 작업 요청의 일정량 모아서 한꺼번에 처리
      * 작업이 완전 종료될 때까지 대기
   - 시분할(time sharing)
      * 여러 작업을 수행할 때 컴퓨터 처리 능력을 일정한 시간 단위로 분할하여 사용
      * 일괄 처리 시스템에 비해 짧은 응답 시간
      * interactive한 방식
   - 실시간(Realtime OS)
      * 정해진 시간 안에 어떠한 일이 반드시 종료됨이 보장
         + Hard realtime system(경성 실시간 시스템)
         + Soft realtime system(연성 실시간 시스템)

**참고할 용어**
>
> MultiTasking : 여러 작업이 동시에 수행되는 것
>
> MultiProgramming : 여러 프로그램이 메모리에 올라가 있음을 강조 => 메모리 강조
>
> Time Sharing : CPU의 시간 분할하여 나누어 쓴다 => CPU 강조
>
> Multiprocess : 여러 프로그램이 동시에 실행
>
> 하나의 CPU
>
> -----
>
> MultiProcessor
>
> - CPU가 여러 개 있는 컴퓨터

**운영 체제의 예**
- UNIX
   * 코드의 대부분 C언어로 작성
   * 높은 이식성
   * 최소한의 커널 구조
   * 소스코드 공개
- MS Windows
   * MS사의 다중 작업용 GUI 기반 운영 체제
   * 불안정성
   * 풍부한 지원 소프트웨어

# CH 2. System Structure & Program Execution

### Computer System Structure


![OS](https://velog.velcdn.com/images/buna1592/post/ad0fc35d-5088-49c7-b589-3db25bc75cf1/image.png)


컴퓨터는 cpu와 Memory로 이루어져 있으며 I/O divice와 상호작용하는 구조를 가짐


**computer**
   - Memory : 사용자 프로그램의 명령어와 데이터를 저장
   - CPU : Memory로부터 명령어를 읽어서 실행
CPU의 연산속도는 매우 빠르기 때문에 시분할 방식(timer 활용)으로 Memory의 프로세스들을 수행한다.<br>
따라서 I/O를 수행해야 할 때 비교적 느린 I/O 장치들을 기다리지 않고 device controller에 요청 후 계속해서 다른 명령어를 수행한다.<br>
후에 I/O작업이 종료 되면 CPU에게 이를 알려주는 과정이 존재하는데 이를 interrupt(cpu에게 신호를 알리는 것)라고 한다.


**I/O Device Controller**
   - 해당 I/O 장치 유형을 관리하는 일종의 작은 CPU
   - CPU와 병렬로 실행되어 메모리 사이클을 놓고 경쟁한다. (누가 메모리에 접근할 것인가)
   - 제어 정보를 위해 control register, status register을 가짐
   - local buffer를 가짐
   - I/O는 실제 device와 local buffer 사이에서 일어남
   - I/O가 끝났을 경우 인터럽트로 CPU에 사실 알림
> device driver(장치 구동기) : OS 코드 중 각 장치별 처리루틴 -> SW
>
> device controller(장치 제어기) : 각 장치를 통제하는 일종의 작은 CPU -> HW


**Mode Bit**
- 사용자 프로그램인지 OS인지 구분하기 위한 비트
- Mode bit을 통해 하드웨어적으로 2가지 모드의 operation 지원 ( 1 사용자 모드, 0 모니터 모드 )


**Timer**
- 정해진 시간이 흐른 뒤 운영체제에게 제어권이 넘어가도록 인터럽트 발생
- 매 클럭 틱 때마다 1감소
- 타이머 0이 되면 타이머 인터럽트 발생
- CPU를 특정 프로그램이 독점하는 것으로부터 보호
- Time Sharing 구현하기 위해 이용됨


### 입출력(I/O)의 수행
모든 입출력 명령은 커널 모드에서만 가능(= 특권 명령)<br>
사용자 프로그램이 입출력 명령을 수행하는 방법
1. 사용자 프로그램은 입출력 명령을 수행할 수 없기 때문에 시스템 콜이라는 입출력 함수를 호출한다.
   + System Call : cpu에게 인터럽트를 발생시켜 cpu제어권을 OS에게 넘기고 mode bit을 0으로 바꾸며 I/O 수행 (운영체제에게 I/O요청)
2. trap을 사용하여 인터럽트 벡터의 특정 위치로 이동
   + trap : sw 인터럽트
3. 제어권이 인터럽트 벡터가 가리키는 인터럽트 서비스 루틴으로 이동
   + 인터럽트 벡터 : 해당 인터럽트의 처리 루틴 주소를 가지고 있음
   + 해당 인터럽트를 처리하는 커널 함수( = 인터럽트의 종류마다 정해진 처리 과정)
4. 올바른 I/O 요청인지 확인 후 I/O 수행
5. I/O 완료 시 제어권을 시스템콜 다음 명령으로 옮김

### DMA(Direct Memory Access)
   - 빠른 I/O 장치를 메모리에 가까운 속도로 처리하기 위해 사용
   - CPU의 중재없이 device controller가 device의 buffer storage의 내용을 메모리에 block 단위로 직접 전송
   - 바이트 단위가 아니라 block 단위로 인터럽트 발생시킴
**CPU는 DMA가 일을 다 하면 한번만 인터럽트 당함.**


### 동기식 I/O 

- I/O 요청 후 입출력작업이 완료된 후에야 제어가 사용자 프로그램에 넘어감
- 방법 1
  - I/O 끝날 때까지 CPU를 낭비시킴
  - 매 시점 하나의 I/O만 가능
- 방법 2
  - I/O 완료될 때까지 해당 프로그램에게서 CPU 빼앗음
  - 다른 프로그램에게 CPU 할당


### 비동기식 I/O
 - I/O 시작된 후 입출력 작업이 끝나기를 기다리지 않고 제어가 사용자 프로그램에 즉시 넘어감.

### **I/O 수행 방식**

1. Memory Mapped I/O
   - 메모리와 I/O가 하나의 연속된 address 영역에 할당된다
2. I/O-Mapped I/O
   - 메모리와 I/O가 별개의 어드레스 영역에 할당되는 것을 의미한다.
  

## 저장장치 계층구조

![OS](https://user-images.githubusercontent.com/33562226/54992343-6c618d80-5002-11e9-96d1-17b9c7bb25df.png)

1. 휘발성
   - 휘발성 저장장치 : 레지스터 / 캐시 / 메인 메모리
   - 비휘발성 저장장치 : 하드디스크 / 광학 디스크 / 자기 테이프 등
2. 속도 
   - 계층이 올라갈수록 액세스 속도가 빠르다.
3. 용량
   - 계층이 올라갈수록 용량이 작고 비싸다.


## 프로그램의 실행

![OS](https://velog.velcdn.com/images/hvyongkim2/post/85a9354d-4496-4cba-a76d-481803b1a838/image.png)

   - 프로그램마다 stack, data, code로 이루어진 Virtual memory를 가지며 필요한 부분을 물리적인 memory에 load하는 과정이 존재
   - Physical memory는 메모리 낭비를 막기 위해 불필요한 부분들을 Swap area에 저장


### 함수

- 사용자 정의 함수
- 라이브러리 함수
  - 프로그램 실행 파일에 포함
- 커널 함수
  - 운영체제 프로그램 함수
  - 커널 함수 호출 = 시스템 콜
