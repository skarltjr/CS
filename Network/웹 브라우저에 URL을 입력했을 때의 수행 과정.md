1. 사용자의 PC는 DHCP 서버에서 사용자 자신의 IP 주소, 가장 가까운 라우터의 IP 주소, 가장 가까운 DNS서버의 IP 주소를 받는다.
2. ARP를 이용하여 IP 주소를 기반으로 가장 가까운 라우터의 MAC 주소를 받는다.
3. 가장 가까운 라우터의 MAC 주소와 IP 주소를 사용해 DNS 서버로 쿼리를 전송하고 URL의 IP 주소를 응답받는다.
4. TCP Socket을 통해 웹 서버와 3 way hand shaking을 하여 연결한다.
5. HTTP Request가 TCP Socket을 통해 보내지고, 응답으로 웹페이지의 정보가 사용자의 PC에 전달

```
DHCP: 호스트의 IP 주소 및 TCP/IP 설정을 클라이언트에 자동으로 제공하는 프로토콜
- Dynamic Host Configuration Protocol
- 즉 IP 자동할당 및 분배기능

DNS: IP 주소와 도메인의 매핑 정보를 관리하는 프로토콜


ARP: IP 주소를 물리적 네트워크 주소로 대응시키기 위해 사용되는 프로토콜
- Address Resolution Protocol

IP 주소: 컴퓨터 마다 부여된 고유의 주소


MAC 주소: NIC 카드 마다 부여된 네트워크 장비 고유의 주소
```
