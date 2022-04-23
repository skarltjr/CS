### ARP란
```
address resolve protocol의 약자로
ip주소를 MAC주소로 변환해준다
```

### MAC
```
단일 디바이스의 고유 식별자로 디바이스마다 존재하는 nic(network interface card)마다 할당
2계층에선 ip주소를 사용할 수 없으며 peer to peer간 접근을 위해 필요하다
```

### ARP
```
ip를 mac주소로 변환해줌으로써 2계층에서 peer to peer간 통신을 가능하게한다.
이때 ip:mac주소를 일대일 대응시켜 테이블로 정리한것이 arp table
```

### arp table생성과정
- <img width="661" alt="스크린샷 2022-04-24 오전 1 10 42" src="https://user-images.githubusercontent.com/62214428/164914148-30a5075e-2a21-4d72-87ef-5527b0f4add0.png">

```
1. pc0이 pc2에게 데이터를 전송하고자한다. 그러나 현재 pc2의 mac주소는알지못한다.
2. 네트워크 구성원에게 arp request를 브로드캐스트하는데 이 때 해당 ip가 자신의것인 pc2는 이거 나야!라고 mac주소를 알려준다
3. 이제 pc2의 mac주소가 arp table에 기록되었고 pc0은 mac주소를 알았으니 접근한다.
```

