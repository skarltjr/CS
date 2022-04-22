### dns란
```
domain name system으로 도메인을 주소로 바꿔주는 시스템
www.naver.com -> 123.456.789.1
```

### dns 동작 과정
```
0. www.naver.com의 ip주소를 알고자한다.
1. 로컬 dns에게 해당 도메인의 ip주소를 물어보고 있으면 반환
2. 없다면 루트 dns에게 물어본다
3. 없다면 recursive query를 통해 최상위 루트dns부터 찾을때까지 하위 dns에게 물어본다
4. 해당 결과를 반환받은 local dns는 결과를 캐싱하고 유저엑 전달
```
