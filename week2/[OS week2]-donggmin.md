| Chapter | Link                                                                                                  |
|---------|-------------------------------------------------------------------------------------------------------|
| 3       | [Part 3](https://possible-ceder-94b.notion.site/Part-3-Process-17f550b0eb03802fb2a0f1eed8ee40bf?pvs=4) |
| 4       | [Part 4](https://possible-ceder-94b.notion.site/Part-4-Process-Management-17f550b0eb038036aad0ea9af63c09a6?pvs=4) |
| 5       | [Part 5](https://possible-ceder-94b.notion.site/Part-5-CPU-Scheduling-17f550b0eb038094bf2ec3dee83e9ea5?pvs=4)     |

## Quiz
1. 프로세스의 state 중에서 Suspended는 일반 state의 차이가 어떻게 되고, suspended로 얻을 수 있는 것은?  
2. 한 프로세스에서 나온 쓰레드들은 무엇을 공유하고, 무엇이 다른가?  
3. 프로세스의 자식 부모 관계는 __구조 이다.  
4. 프로세스에서 folk() 실행 시, 자식 프로세스는 부모 클래스의 Program counter와 같을까?  
5. 다음 코드를 실행했을 때 출력값을 말하여라.
   ```c
   // parent.c
   #include <stdio.h>
   #include <unistd.h>

   int main() {
       int pid;
       printf("Start\n");
       pid = fork();

       if (pid > 0) { // 부모 프로세스
           printf("Parent Process: pid = %d\n", pid);
       } else if (pid == 0) { // 자식 프로세스
           printf("Child Process\n");
           execl("/bin/echo", "echo", "Hello from execl!", NULL);
           printf("This will not be printed if execl is successful\n");
       } else { // fork 실패
           printf("Fork failed\n");
       }
       return 0;
   }
6. SRTF의 문제점 2가지는?
7. 다음은 네 개의 프로세스가 실행되는 상황이다. 각 프로세스의 도착 시간, 실행 시간, 그리고 우선순위가 아래와 같이 주어졌다.
   
  
| Process | Arrival Time | Burst Time | Priority (1 = High) |
|---------|--------------|------------|---------------------|
| P1      | 0            | 5          | 2                   |
| P2      | 1            | 3          | 1                   |
| P3      | 2            | 8          | 3                   |
| P4      | 3            | 6          | 2                   |

---

아래의 CPU 스케줄링 알고리즘에 따라 프로세스가 실행되는 각 프로세스의 평균 대기 시간과 평균 반환 시간을 계산.

1. **FCFS** (First-Come, First-Served)
2. **SJF** (Shortest Job First) - 비선점
3. **Priority Scheduling** - 비선점
4. **Round Robin** (Time Quantum = 2)

