### Tread safe하다란?
```
멀티 스레드 환경에서 여러 스레드가 동시에 하나의 변수, 함수 혹은 객체에 접근하더라도 애플리케이션 실행에
문제가 없는 것을의미한다

나아가 하나의 스레드가 A함수를 실행중일 때 다른 스레드가 A함수를 호출하여 실행해도 각각 올바른 결과를 도출한다

다만 
```

### Tread safe하게 구현하는 방법은?
```
1. stateless
- 현재 factorial() 매서드는 stateless
- 어떠한 input이 들어오든 input을 활용할 뿐 매서드 자체에서 의존적인 변수나 상태를 보존하고있지 않다.
public class MathUtils {
    
    public static BigInteger factorial(int number) {
        BigInteger f = new BigInteger("1");
        for (int i = 2; i <= number; i++) {
            f = f.multiply(BigInteger.valueOf(i));
        }
        return f;
    }
}
```

```
2. immutable
- String은 불변
- 만약 어떠한 객체가 불변이라면 해당 객체를 여러곳에서 동시에 접근하여 사용한다해도 문제가 생길 위험이 없다
- 왜? 절대 변하지 않으니
public class MessageService {
    
    private final String message;

    public MessageService(String message) {
        this.message = message;
    }
    
    // standard getter
    
}
```
```
3. lock
- 공유자원을 꼭 사용해야한다면 해당 자원 접근을 락으로 통제할 수 있다.
- 다만 락을 사용한다는것은 동시 접근 문제를 해결하기위해 어느정도 동시성을 포기해야할 수 있다
```
jpa의 락https://github.com/skarltjr/Memory_Write_Record/issues/89
    
