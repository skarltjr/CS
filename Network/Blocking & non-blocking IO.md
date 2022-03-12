### Blocking & non-blocking I/O.md
```
I/O작업은 오로직 kernel level에서만 수행이 가능하다
따라서 프로세스 / 스레드는 커널에게 I/O를 요청해야 한다.
```

### 1. blocking i/o
- <img width="731" alt="스크린샷 2022-03-12 오후 2 05 06" src="https://user-images.githubusercontent.com/62214428/158004622-10509a9f-5b9b-411d-b594-400beab58c20.png">
```
1. process( or thread)가 kernel에게 i/o를 요청하는 함수 호출
2. kernel이 작업을 완료하면 결과를 리턴받는다.

★blocking i/o
- i/o작업이 진행되는 동안 user process( or thread)는 자신의 작업을 중단시킨채 대기
- resource 낭비가 심하다

★만약 여러 client가 접속하는 서버를 이러한 blocking i/o로 구현하게되면
- 클라이언트의 요청 -> i/o를 위해 현재 작업 중지 -> i/o종료 후 작업 진행
- 이 때 클라이언트 a의 요청으로 i/o를 진행하게 될 때 b의 작업도 중단되면 안되니까 클라이언트마다 thread 발급
- 엄청난 자원 소모
```

### 2. non-blocking i/o
- <img width="761" alt="스크린샷 2022-03-12 오후 2 05 11" src="https://user-images.githubusercontent.com/62214428/158004625-44cc6bf6-7ae9-4f5e-a7a3-61540b071993.png">

```
i/o 작업이 진행되는 동안 user작업을 중단하지 않는다

1. 유저 프로세스는 recvfrom함수를 호출하여 커널에게 해당 소켓으로부터 데이터를 받아오고 싶다고 요청. 
2. 커널은 이 요청에 대해서 상대방의 데이터를 전송 받아서 recvBuffer에 저장하고, 유저에게 그 내용을 복사해준다. 
3-1. 상대방으로부터 데이터를 받는 중에 recvBuffer가 비어있다면 유저 프로세스가 커널에게 받아올 수 있는 정보는 없다. 
     따라서 recvfrom 함수는 아직 작업 진행중이란 의미로 "EWOULDBLOCK"을 리턴한다.
     이 결과를 받은 유저 프로세스는 다른 작업을 진행할 수 있다.
3-2. 만약 recvBuffer에 유저가 받을 수 있는 데이터가 있다면, 버퍼로 부터 데이터를 복사하여 받아온다. 
     recvBuffer는 커널이 가지고 있는 메모리에 적재되어 있으므로 메모리간 복사가 일어나 I/O보다 훨씬 빠른 속도로 데이터를 받아올 수 있다. 
     이때 recvfrom함수는 빠른 속도로 읽을 수 있는 데이터를 복사해주고 복사한 데이터의 길이와 함께 반환한다. 
     위의 모든 반환이 I/O의 진행시간과는 관계없이 빠르게 동작하기 때문에, 유저 프로세스는 자신의 작업을 오랜시간 중지하지 않고도 I/O 처리를 수행할 수 있다.


```
