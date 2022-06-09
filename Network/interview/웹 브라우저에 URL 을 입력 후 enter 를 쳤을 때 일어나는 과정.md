## 웹 브라우저에 URL 을 입력 후 enter 를 쳤을 때 일어나는 과정
```
1. 유저가 url을 입력한다
2. url에 해당하는 ip를 찾기위해 캐쉬에서 dns 기록을 확인한다.
  - 있다면 3번
  - 없다면 루트 dns에게 해당 url의 ip를 알려달라고 요청한다.
  - 루트 dns는 재귀적 query를 통해 하위 dns로부터 ip를 확인하고 이를 반환해준다
3. target ip를 확인
4. 라우터를 통해 source to target 최적 경로를 찾아 접근한다
5. tcp - 3 way handshake를 통해 연결을 요청 및 연결
6. http 통신은 클라이언트 연결 - 응답 - 연결 종료로 요청에 대한 응답을 받은 후 4 way handshake를 통한 연결 종료
```
- 참고 : https://velog.io/@khy226/브라우저에-url을-입력하면-어떤일이-벌어질까
