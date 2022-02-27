1. 조인이란?
```
두개이상의 테이블을 연결하여 데이터를 활용하는 방법
```
<img width="525" alt="스크린샷 2022-02-28 오전 12 07 16" src="https://user-images.githubusercontent.com/62214428/155887832-82a33f3b-9bf2-488b-8aaf-0e6bbbcedd54.png">


2. inner join
```
두 테이블간 교집합을 얻어내겠다.
즉 a테이블과 b테이블이 모두 갖고 있는 정보를 검색

select a.*,b.age from customer a join sales b on a.customerId=b.customerId;
-> customer가 물건을 구매했다면 Sales가 생성되었을 것
-> 즉 ★모든 고객과 모든 구매정보가 아닌
-> 고객 중 구매를 한 사람. 고객이자 구매를 한 교집합을 찾아내는 것
```

3. left/right outer join
```
고객 정보 입장에서 2번은 모든 고객이 아닌 고객 중 한 번이라도 구매를 한 고객의 정보만 얻어낼 수 있다.
그런데 나는 지금 기본적으로 모든 고객을 대상으로 하되 구매를 했다며 구매정보까지 알고자한다.
즉 왼쪽에 해당하는 고객정보는 모두가져오고 구매를 했다면 고객의 구매정보까지 추가하여 가져오겠다.

select a.customerName,b.* from customer a left join sales b on a.customerId=b.customerId;
```

4. full outer join
```
a테이블과 b테이블 모두를 가져오겠다
사실상 기준테이블의 의미가 없다.
```

5. cross join
<img width="451" alt="스크린샷 2022-02-28 오전 12 23 50" src="https://user-images.githubusercontent.com/62214428/155888474-7a37c13b-1a33-4072-90fe-c62fcd3aab67.png">

```
모든 경우의 수를 표현
n*m개의 결과

select a.name,b.age from table1 a cross join table2 b
```

6. self join
```
자기자신을 조인한다
하나의 테이블을 여러번복사해서 조인
자신이 갖고 있는 컬럼을 다양하게 변형시켜 활용할경우에 사용

select a.*,b.* from mytable a, mytable b
```
