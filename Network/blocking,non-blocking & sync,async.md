### blocking,non-blocking & sync,async

### 1. blocking VS non-blocking
```
blocking과 non-blocking의 가장 큰 차이는 `호출된 함수`가 `호출한 함수`에게 제어권을 주는지 차이.

ex) 함수a가 함수b를 호출한 경우
- blocking : b는 자신의 일을 다 끝낼때까지 제어권을 갖는다.
             즉 a는 b의 작업을 기다려야한다.
- non-blocking : b는 자신의 할 일을 끝내지못했어도 제어권을 a에게 전달한다.
                즉 a는 b를 기다리면서 자신의 할 일을 수행할 수 있다.       
```

### 2. synchronous VS asynchronous
```
⭐️ 동기 : 호출한 함수와 응답을 받는 함수가 동일하다
⭐️ 비동기 : 호출한 함수와 응답을 받는 함수가 동일하지 않아도 된다. 즉 호출시점과 처리결과에 대한 응답시점이 같지 않다.

동기 / 비동기는 `동시성`에 주목하자
함수 A와 B가 존재할 때 B의 수행결과나 종료 상태를 A가 계속 신경쓰고 있는 상태가 sync! 신경쓰지 않으면 async


ex) 함수a가 함수b를 호출한 경우
- 함수 b의 상태에 대해 신경쓰지 않고 a는 자신의 일을 하는것이 async
- b는 자신의 작업 완료 상태를 a에게 callback으로 전달한다
```

### 3. 비교해보기
- <img width="1039" alt="스크린샷 2022-03-11 오후 8 25 37" src="https://user-images.githubusercontent.com/62214428/157858301-d9019854-ed30-4639-97e4-66ac4fc812fe.png">
```
1 | 2
-----
3 | 4

1. sync & blocking
- read() / write()
- blocking이기 때문에 호출된 함수에게 제어권이 존재

2. sync & non-blocking
- 논블러킹 모드의 read() / write()
- non-blocking이기 때문에 호출한 함수도 호출된 함수도 각자의 일을 수행
- sync이기 때문에 호출한 함수는 지속적으로 호출된 함수의 상태 체크
- non-blocking read()에서 데이터가 있는지 지속적으로 확인하면서 있으면 읽고 없으면 리턴하는 ..

3. async & blocking
- blocking이기 때문에 호출된 함수의 작업동안 호출한 함수의 작업 중단
- async이기 때문에 호출한 함수는 호출된 함수를 신경쓰지 않으며
- 호출된 함수는 자신의 작업 종료 상태를 콜백으로 전달

4. async & non-blocking
- non-blocking이기 때문에 호출한 함수와 호출된 함수모두 자신의 작업수행
- async이기 때문에 호출한 함수가 호출된 함수를 신경쓰지 않으며 호출된 함수는 자신의 작업 종료 상태를 callback으로 전달
```

예시 참고 : https://musma.github.io/2019/04/17/blocking-and-synchronous.html
