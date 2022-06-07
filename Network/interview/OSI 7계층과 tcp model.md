## OSI 7계층과 tcp model에 대해 설명해주세요
- https://github.com/skarltjr/CS/blob/main/Network/OSI%207%20layer.md
- https://github.com/skarltjr/CS/blob/main/Network/TCP%20VS%20UDP비교.md

```
osi 7계층은 통신이 일어나는 과정을 7단계로 분리한것으로 이상이 생긴곳을 분명히 파악하고자..

1계층 physical layer는 peer to peer간 물리적으로 연결되어 실제 데이터 전달

2계층 link layer는 peer to peer간 연결성 보장
mac주소로 통신, 에러검출, ack 매커니즘을 통한 오류제어

3계층 network layer는 end to end간 연결성 제공
ip와 라우터를 통해 말단간 연결을 제공
라우터를 통해 최적의 경로 탐색

4계층 transport layer는 end to end간 연결성 보장
신뢰성과 연결지향적인 TCP프로토콜
비신뢰성, 비연결지향 UDP프로토콜

5계층 session layer는 데이터가 통신하기 위한 논리적 연결을 담당
TCP/IP 세션 생성 제거 역할

6계층 presentation layer는 데이터 표현 및 암호화
파일 인코딩, 압축, 암호화등

7계층 application layer는 최종 목적지로 응용프로그램과 관계하여 전달받은 데이터를 실질적으로 사용
```


```
tcp란 1:1 연결 지향적 프로토콜
연결 = 3 way 종료 = 4 way handshake
신뢰성있는 데이터 전송 보장
- 순서 보장
- 누락 데이터 재전송
- timeout시 재전송
흐름제어 및 혼잡제어

흐름제어
- 송신측과 수신측의 데이터처리 속도 차이에 인해 발생하는 문제 해결
- 동일한 크기의 윈도우 사이즈를 약속하고 이 크기만큼의 데이터를 다룬다.
- 만약 n개 전달하고 잘 받았다면 다음 n개로 넘어간다

혼잡제어
- 송신측에서 네트워크 상태를 스스로 파악하여 네트워크 부하를 방지한다.
- additive increase multiplicative decrease
- 윈도우 크기를 1씩증가시키다 만약 누락,재전송이 발생한다면 이 크기는 네트워크의 부하를준다는것
- 따라서 절반으로줄인다.
- 그러나 초기 시작이 느리기에 slow start방법으로 윈도우 크기를2배씩증가시킨다
- 다만 이땐 금방 임계점에 도달하니 과감하게 1로줄인다.
```


