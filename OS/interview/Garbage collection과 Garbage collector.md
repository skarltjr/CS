## Garbage collection이란?
```
참조가 끊긴, 더 이상 사용되지 않은 메모리 중 회수되지 않은 부분을 회수함으로써 메모리 누수를 막는다
참조가 끊기 객체를 찾는것이아니라 참조되고 있는 객체를 찾고 나머지 객체는 참조가 끊긴것이니 회수한다

객체가 참조되고 있음을 판단하는 방법은 Reachability로 객체들은 서로 다른 객체를 참조하는 사슬 구조를 이루기에
유효한 참조가 있다면 말 그대로 살아있는 객체 아니면 garbage
```

## Garbage collector란?
```
Garbage collection을 수행하는 주체로
1. heap영역에 존재하는 객체들에 대해 접근 가능한지 파악(사용되는지)
2. root부터 시작하여 접근 가능한 객체들에 대해 Mark - Mark
3. Mark되지 않은(접근 불가능한) 객체를 메모리에서 제거 - Sweep
4. 중간중간 발생한 메모리 단편화를 Compact - Compact

자바 GC에는 크게 4 종류가 있다.


1. serial GC
- 가장 초기 방식으로 단일 스레드로 동작
- 하나의 스레드로 애플리케이션 실행 & GC을 수행
- stop the world가 발생하고 이 때 애플리케이션 실행이 멈춰야한다

2. parallel GC
- 멀티 스레드를 활용(young 영역에서만)
- serial GC에 비해 stop the world가 짧다
- 그러나 여전히 애플리케이션 실행이 멈추는 시간은 존재

3. parallel old GC
- old영역까지 멀티 스레드를 활용

4. CMS GC
- initial mark : stop the world 발생 / 클래스 로더에 가장 가까운 객체 중 살아있는 객체를 찾는다
- concurrent mark : stop the world가 발생 x / initial mark에서 찾은 객체들을 참조하는 객체가 살아있는지 추가 파악
- remark : stop the world발생 / concurrent mark에서 새로 추가되거나 참조 끊긴 객체를 확인
- concurrent : stop the world 발생 x / 사용중인 객체를 제외한 나머지 쓰레기를 회수한다.
```
