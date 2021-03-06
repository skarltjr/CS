### CPU scheduling
```
스케줄링: CPU를 효율적으로 사용하기 위해 프로세스를 잘 배정하는것

목표:
- batch system : 가능한 많은 일을 수행
- interactive system : 빠른 응답시간, 적은 대기시간
- real-time system : 기한 맞추기
```
### 선점 / 비선점 스케줄링
- 선점 : os가 cpu의 사용권을 선점할 수 있다, os가 cpu를 강제로 회수할 수 있다.
- 비선점 : 프로세스 종료 or I/O 등의 이벤트가 있을 때까지 실행 보장 

### 프로세스 상태
- <img width="908" alt="스크린샷 2022-03-21 오전 11 53 34" src="https://user-images.githubusercontent.com/62214428/159199370-057f5ca1-d01c-4b51-bde7-3990cc059b50.png">
```
- 스케줄러 디스패치(scheduler dispatch) : 준비 상태의 프로세스 하나를 선택하여 실행
- 인터럽트 : 예외, 입출력, 이벤트 등이 발생하여 현재 실행중인 프로세스를 ready 상태로 바꾸고 해당 작업을 먼저 처리
       - 이 경우 프로세스는 ready상태가 되고 다시 스케줄러에 의해 cpu를 할당받을때 작업 재진행
- I/O event wait : 실행중인 프로세스에서 입출력이나 이벤트가 발생하는 경우 입출력/이벤트가 끝날때까지 대기 상태로 변환
- I/O event completion : 입출력/이벤트가 끝난 프로세스 재가동을 위해 프로세스를 ready상태로 전환하여 cpu를 할당받을 수 있도록.
    
```
### CPU 스케줄링 종류
#### 비선점 스케줄링
1. FCFS ( First Come First Served )
```
큐에 도착한 순서대로 CPU 할당
만약 실행시간이 짧은게 큐에 늦게 들어오고 실행시간이 긴게 먼저 들어오는 경우 평균 대기 시간이 길어진다. 
```
2. SJF ( Shortest Job First )
```
수행시간이 짧다고 판단되는 작업 우선 처리
평균 대기 시간이 줄어들 순 있지만 만약 짧은 작업이 계속 들어오면 작업 시간이 긴 프로세스가 영원치 처리되지 못한다.
```
3. HRN ( highest response-ratio next )
```
우선순위를 계산하여 점유 불평등 보완
우선순위 = (대기시간 + 실행시간)/(실행시간)
```
#### 선점 스케줄링
1. priority scheduling
```
정적/동적으로 우선순위를 부여하여 우선순위가 높은 순서대로 처리
우선순위가 낮은 프로세스는 무한정 대기하는 starvation 발생가능
이를 방지하기 위해 한 번씩 낮은 우선순위의 프로세스를 끌어올려 실행하는 aging
```
2. rounb robbin / rr
```
큐에 들어온 모든 프로세스는 정해진 작업 시간동안만 cpu를 점유가능 이 후 회수하여 다음 프로세스 진행

만약 이 cpu 점유 가능한 ㅅㅣ간이 길면 FCFS랑 똑같고
점유 가능한 시간이 짧으면 context switching 오버헤드가 크다
```
3. multilevel-queue
- <img width="582" alt="스크린샷 2022-03-21 오후 12 19 16" src="https://user-images.githubusercontent.com/62214428/159200955-e422fe9e-c0fb-4672-9c37-f33b8e171faf.png">

```
- 작업들을 여러 그룹의 큐에 insert
- 우선순위가 낮은 큐의 프로세스들은 긴 cpu 점유시간을 갖고
- 우선순위가 높은 큐의 프로세스들은 짧은 cpu점유시간을 갖도록 함으로써 우선순위가 낮은 큐의 프로세스가 실행되지 않는 문제 극복
```
4. multilevel-feedback-queue
- <img width="509" alt="스크린샷 2022-03-21 오후 12 23 41" src="https://user-images.githubusercontent.com/62214428/159201340-f93c72a8-14df-4bf2-91bc-eaf771438970.png">

```
- 다단계 큐에서 만약 프로세스가 자신에게 할당된 cpu 점유 시간을 다 채우면 우선순위가 한단계 낮은 큐로 이동
       - (할당된 시간을 다 썼는데도 처리가 안됐다면 꽤 무거운 작업이라 판단하여)
- 다 채우지 못했다면 현재 큐에 그대로
- 짧은 작업에 유리하고 처리 시간이 짧은 프로세스를 먼저 처리하기 때문에 turnAround 평균 시간을 줄여준다
```
### CPU 스케줄링 척도
```
Response Time
 작업이 !처음 실행! 되기까지 걸린 시간
 
Turnaround Time
 실행 시간과 대기 시간을 모두 합한 시간으로 !작업이 완료!될 때 까지 걸린 시간
```




