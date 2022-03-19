## PCB & context switching

### process management
```
CPU가 프로세스가 여러개일 때 CPU 스케줄링을 통해 관리하는것
```
- 이 때 cpu는 각 프로세스들이 누구인지 알아야 관리가 가능
- 이러한 프로세스 정보가 바로 `process metadata`
```
Process Metadata

Process ID
Process State
Process Priority
CPU Registers
Owner
CPU Usage
Memeory Usage
```
- ★이 process metadata가 저장되는곳이 바로 `PCB( process control block) `

### pcb
- `프로세스 메타데이터가 저장되는 곳`
- `하나의 pcb에는 하나의 프로세스 metadata만 저장`
- <img width="587" alt="스크린샷 2022-03-19 오후 2 00 36" src="https://user-images.githubusercontent.com/62214428/159107605-51d25ecd-cc6b-47bd-bf5c-9f15ac58435b.png">
```
프로그램 실행 -> 프로세스 생성 -> 프로세스 주소 공간(code,data,stack) 생성
-> 이 프로세스의 metadata가 pcb에 저장
```

### context switching
```
여러 프로세스가 처리되야 하는 상황에서 
cpu가 이전 프로세스 상태를 pcb에 보관하고, 다음으로 진행할 프로세스 정보를 pcb에 읽어 레지스터에 적재하는 과정
```
- 인터럽트 발생, 실행 중인 cpu 사용 허가시간으 모두 소모, 입출력을 위해 대기해야하는 경우 context switching 발생

### context switching overhead
- <img width="505" alt="스크린샷 2022-03-19 오후 2 27 35" src="https://user-images.githubusercontent.com/62214428/159108405-4bb58175-ee15-42a6-8c94-8be7368f644d.png">
```
컨텍스트 스위칭이 잦아진다는것은 process0의 metadata를 pcb0에 저장, process1의 metadata를 pcb1에 load와 같은 경우가 빈번해진다는것
즉 이 과정에서 PCB를 저장하고 가져올 때 CPU는 아무런 일도 하지 못하게 된다. 이것이 바로 오버헤드

스레드가 프로세스보다 컨텍스트 스위칭면에서 우수한 이유는 공유부분이 존재하기때문
```
