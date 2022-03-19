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

