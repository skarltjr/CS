### 인덱스란
```
rdbms에서 검색속도를 높이기 위해 사용하는 기술
index는 색인. 해당 table의 컬럼을 색인화 ( 따로 파일로 저장 )하여 검색시 해당 table의 레코드를 full scan이 아닌
색인화 되어있는 index 파일을 검색하여 검색속도를 빠르게한다.

마치 큰 책 맨앞에 목차가 존재하고 이 목차를 통해 좀 더 빠르게 해당 페이지에 접근하듯이★

index는 tree구조로 색인화
B+ Tree를 사용 / balance search tree
```
<img width="405" alt="스크린샷 2022-02-28 오후 6 18 10" src="https://user-images.githubusercontent.com/62214428/155956866-07b7ec2f-460b-4d9c-8f25-be192a4a134a.png">
찾고자하는것이 1번이라면 첫블럭에 1번이 포함된걸 알기에 full scan할 필요없이 1번이 포함된 첫 블럭으로 바로 접근할 수 있다.


### 인덱스의 원리
```
index를 해당 컬럼에 주게 되면 초기 table생성시 만들어진 MYD,MYI,FRM 3개 파일 중 MYI에 해당 컬럼을 색인화

그래서 select로 인덱스를 활용하는 컬럼을 쿼리할 때 해당 table을 full scan하는것이 아닌 앞서 만들어진 
MYI파일에 접근하여 내용 검색

즉 책 내용을 찾기위해 모든 페이지를 확인하는것이 아닌 목차를 통해 빠르게 접근
```

### 인덱스의 장점
```
- 키 값을 기초로 하여 테이블에서 검색과 정렬 속도를 향상시킵니다.
- 질의나 보고서에서 그룹화 작업의 속도를 향상시킵니다.
- 인덱스를 사용하면 테이블 행의 고유성을 강화시킬 수 있습니다.
```

### 인덱스의 단점
```
- 가장 큰 단점으론 인덱스 된 필드의 데이터를 수정 및 삭제할 때 성능이 저하
  - 따라서 데이터의 변경보다 조회가 많은곳에서 효율적인 기술
- 인덱스 생성으로 인해 추가적인 공간차지 및 인덱스 생성 소요 시간 증가
- 데이터 변경이 빈번한 경우 인덱스를 재작성할 필요가 있어 성능에 영향
```

### 언제 사용할까??
```
사용
- 데이터의 수정보다 조회가 주가되는 컬럼
- where 조건절에 자주 사용되는 컬럼 
- 변경이 적은 컬럼


사용 x
- 수정이 빈번한 컬럼
- 데이터의 중복도가 높은 컬럼(ex. 성별같은 경우 남,여만 존재하여 인덱스의 효율이 매우 낮다)
```
### B-Tree
- <img width="851" alt="스크린샷 2022-04-02 오후 6 25 56" src="https://user-images.githubusercontent.com/62214428/161376853-ce721c78-b87b-40c3-a0da-3c47fd5b52cb.png">
- 자식 노드가 두 개 이상
- 하나의 `노드`에 `여러개의 데이터`
- 노드의 데이터는 항상 `정렬된 상태`
- 한 노드에 최대 M개의 데이터 저장할수 있으면 M차 B-Tree
```
트리 구조를 활용하기 때문에 선형 탐색보다 탐색에 이점
```

### B+Tree
- <img width="941" alt="스크린샷 2022-04-02 오후 6 26 18" src="https://user-images.githubusercontent.com/62214428/161376865-3cedc24a-b6a3-4824-b708-8efa87bb27a4.png">
- B-Tree 확장 개념
- ⭐️노드에 `key`만 담아두고, `leaf 노드`에 `key와 data` 저장
- 즉 모든 값은 leaf에만 있고, 나머지는 데이터를 찾기 위한 방향성을 제공
- 리프 노드끼리 Linked List로 연결되어있다
```
왜 B+Tree를 사용하는가? 
장점이 무엇인가?

1. 리프 노드를 제외한 다른 노드에는 key만 존재한다고 했다. 
  - 즉 하나의 노드에 많은 key를 담을 수 있어서 트리의 높이가 낮아진다. / cache hit 
  
2. full scan 시 
  - b-tree는 데이터가 여기저기 퍼져있어 모든 노드 탐색해야한다
  - b+tree는 데이터가 오로지 말단노드에만 있고 이 말단 노드는 모두 연결되어있다. 따라서 말단 노드 한 번의 선형탐색만 필요
```
