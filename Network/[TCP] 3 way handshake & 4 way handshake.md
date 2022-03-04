### [TCP] 3 way handshake & 4 way handshake
```
TCP의 연결과 연결종료의 과정
tcp는 end to end간 안정적이 데이터 통신을 보장한다
```

#### 1. 3 way handshake - 연결
- <img width="497" alt="스크린샷 2022-03-04 오후 1 50 10" src="https://user-images.githubusercontent.com/62214428/156701442-2739ad3c-30f9-45c4-b67e-1a98b8acb86f.png">
```
1. 클라이언트가 서버에게 SYN 패킷을 전달 / 나 요청보내도 될까??
2. 서버는 SYN을 받고, 클라이언트에게 이에 대한 응답으로 ACK과 SYN패킷을전달 / 응 요청보내도 돼~
3. 클라이언트는 서버의 응답인 ACK과 SYN 패킷을 받고 이에 대한 응답 ACK을 전달 / 알겠어 보낼게~
  - 이 때 클라이언트는 ACK과 함께 보내고자 하는 데이터를 전송할수도 있다.
이러한 TCP의 연결방식이  3 way handshake 
```


#### 2. 4 way handshake - 연결 종료
- <img width="478" alt="스크린샷 2022-03-04 오후 1 50 14" src="https://user-images.githubusercontent.com/62214428/156702078-f4566c84-036c-4f0a-9c5b-9c03ed6bd59a.png">
```
1. 클라이언트는 서버에게 연결 종료 FIN플래그를 보낸다 / 나 연결 종료할게~
2. 서버는 FIN을 받고 확인했다는 ACK을 응답으로 보낸다 / 일단 알겠어~
  - 이 때 서버는 read버퍼는 종료하고 데이터를 다 보내고 write버퍼르 닫는다
3. 서버는 데이터를 다 보낸후 연결을 종료하기 위해 클라이언트에게 FIN을 보낸다 / 나도 끝낼게~
4. 클라이언트는 FIN을 받고 확인했다는 ACK을 서버에게 보낸다 / 알겠어~
  - 클라이언트는 1번 후 time_wait으로 서버로부터 다 못받은 데이터를 받기위해 대기하고 있었다.
  - 서버는 클라이언트에게 ACK을 받은 후 완전 종료 / 소캣 종료
  - time_wait 후 클라이언트도 종료
  
 통신 종료
```
