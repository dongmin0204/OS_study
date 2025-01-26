| Chapter | Link                                                                                                  |
|---------|-------------------------------------------------------------------------------------------------------|
| 6-1       | [Part 6-1](https://possible-ceder-94b.notion.site/Part-6-Process-Synchronization-17f550b0eb0380488838f8716f286ef3?pvs=4) |
| 6-2       | [Part 6-2](https://possible-ceder-94b.notion.site/Part-6-Process-Synchronization-2-17f550b0eb0380f2a579f869238986c8?pvs=4) |

## Quiz
1. 세마포어의 P 연산과 V 연산의 기능과,  세마포어를 이용하여 프로세스 동기화를 구현하는 기본적인 방식은?
2. Race Condition은 언제 발생하는 가?
3. 모니터를 사용하여 프로세스 동기화를 구현할 때의 장점은?
4. 다음은 공유 버퍼의 의사 코드이다.  
    a. 빈칸을 채우시오
    
    ```c
    void* producer(void* arg) {
        int item;
        while (1) {
            item = produce_item();
            
            sem_wait(&empty);
            pthread_mutex_lock(&mutex);
            
            buffer[in] = item;
            in = /*빈칸*/
            
            pthread_mutex_unlock(&mutex);
            sem_post(&full);
        }
    }
    
    void* consumer(void* arg) {
        int item;
        while (1) {
            sem_wait(&full);
            pthread_mutex_lock(&mutex);
            
            item = buffer[out];
            out = /*빈칸*/
            
            pthread_mutex_unlock(&mutex);
            sem_post(&empty);
            
            consume_item(item);
        }
    }
    ```
    
    b. 위의 공유 버퍼의 문제점을 찾고, 해결방안은?
