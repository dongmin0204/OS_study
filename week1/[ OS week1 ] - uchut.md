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
