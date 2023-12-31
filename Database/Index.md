# Index

> 책의 색인과 같은 기능 
Index를 검색하여  해당 자료의 테이블을 엑세스 하는 방법
> 

### 데이터 베이스의 테이블파일 구성

- FRM : 테이블 구조 저장 파일
- MYD : 실제 데이터 파일
- MYI : Index 정보 파일

INDEX을 사용하는 순간 MYI를 활용한다.

Index는 항상 정렬된 상태로 존재한다.

공간 성능을 포기하고 검색속도를 얻는다.

### Index 장점

- 테이블 조회 속도의 증가

### Index 단점

- 병행정 저하
- 업데이트 및 record 삭제 추가시 성능 저하 (DML에 취약)
    - `Insert` : 기존 block에 여유가 없을 때 새로운 block을 할당 한후 key를 새로 옮긴다.
    - `Date` : table data가 delete 된다면 단순히 data를 지우고 다른 얘가 사용가능  |  
                 index data가 delete 된다면 data는 지워지진 않지만 사용안됨 표시만
    - `Update` : Index는 update가 불가능하다. delete → insert 작업 순으로 처리
- Table의 Data ≠ Index의 Data

### Index를 사용하면 좋은 경우

- 규모가 작은 테이블
- DML이 별로 사용되지 않는 테이블
- JOIN, WHERE 등이 자주 사용되는 컬럼

## 인덱스의 자료구조

### HashTable

- hashtable은 빠르다…
- 하지만 해시는 (=) 연산에만 특화되어 있다.
    - 값이 1만 달라져도 완전히 다른 값을 보유하는데 부등호 연산(> , <) 을 자주 사용하는 데이터베이스의 검색에는 적합하지 않다.

### B Tree

- 자식이 둘 이상 있을 수 있는 균형 트리
- O(log N)

### B+ Tree

- B Tree 개선
- 값을 리프노드에만 저장하고 리프노드는 연결리스트로 연결되 있는 상태