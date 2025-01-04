# CH 1. Introduction to Operating Systems
**운영체제란?**

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
**컴퓨터 시스템 구조**

![OS](https://blog.kakaocdn.net/dn/c14Gr5/btrUIm1wbB1/I9StliVDlL8GQwHStpqTuK/img.png)
