### IPC
- `inter process communication`
```
프로세스는 독립적으로 실행된다. 즉 서로 다른 프로세스에게 영향을 받지 않는다
프로세스는 각각 개별적인 자원 및 주소공간을 사용
- 반면 스레드는 스택을 제외한 부분을 공유하기 때문에 다른 스레드에게 영향을 받는다.
```
- 이러한 상황에서 프로세스간 통신이 필요한 상황도 존재할텐데.. 이를 가능하도록 해주는것이 바로 IPC통신

### 어떻게 프로세스간 통신이 이뤄지는가?
```
커널이 제공하는 IPC 설비를 이용해 통신
```

### IPC 종류
1. 익명 PIPE
- ![KakaoTalk_Photo_2022-03-20-13-48-28](https://user-images.githubusercontent.com/62214428/159148679-3ce3d359-1c30-411a-ae55-20907e0232ba.jpeg)
```
파이프는 프로세스간 단방향 통신을 지원하는 파일
매우 간단하게 사용할 수 있는 장점이 있고, 단순한 데이터 흐름을 가질 땐 파이프를 사용하는 것이 효율적이다. 
단점으로는 전이중 통신을 위해 2개를 만들어야 할 때는 구현이 복잡해지게 된다.
```
2. named pipe(FIFO)
```
익명 파이프는 (부모-자식)처럼 통신할 프로세스를 명확히 알 수 있는 경우에 사용
반면 named pipe는 전혀 모르는 프로세스간 통신에 사용
1번의 pipe와 기능자체는 동일 but 통신을 위해 이름있는 파일을 사용
```
3. message queue
```
named pipe처럼 선입선출 방식으로 통신
차이점은 Named PIPE가 데이터의 흐름이라면 메세지 큐는 메모리 공간이라는 점. 
이는 여러개의 프로세스가 메세지 큐의 데이터에 접근할 수 있음을 의미
```
4. 공유 메모리
```
프로세스는 기본적으로 독립적인 주소 공간을 할당받지만 
예외적으로 공유메모리는 프로세스간 메모리 영역을 공유해서 사용할 수 있도록 지원
프로세스가 커널에게 공유 메모리 할당을 요청 -> 모든 프로세스는 해당 메모리 영역에 접근 가능

★모든 프로세스가 공유 메모리에 바로 접근할 수 있기 때문에 프로세스 통신 중 가장 빠르다
```
5. 메모리 맵
```
공유 메모리처럼 메모리를 공유
메모리 맵은 열린 파일을 메모리에 맵핑시켜서 공유하는 방식이다. (즉 공유 매개체가 파일+메모리)

주로 파일로 대용량 데이터를 공유해야 할 때 사용한다.
```
6. 소캣
```
네트워크 소켓 통신을 통해 데이터를 공유
```

