## SQL Style Guide
(공통된 작성 규칙을 제공하고자 SQL 가이드 작성 했습니다.)

* 필드 명명 및 참조 규칙
 * table, column, 변수(Alias)는 소문자로 작성하고 그 이외의 내역은 대문자로 통일하여 작성한다.

 * 모호한 값은 식별할 수 있는 네이밍을 접두어로 사용한다.  
 [generally ambiguous value -> should always be prefixed by what it is identifying or naming]

 * 모든 컬럼 명은 snake case로 표현한다.  
   [All field names should be snake-cased(CamelCaseX)]
 * 예시코드
 ```
 [good]
 SELECT id   AS account_id,
           name AS account_name,
           ...
      FROM bank
      -------------------------
 [bad]
 SELECT id,
           name,
           type
           ...
 ```

* JOIN 규칙
 * JOIN 서술부(ON 조건절)와 비 JOIN 서술부(WHERE 조건절) 분리시켜 가독성 향상
 ```
 [good]
 SELECT cust_seq  
      FROM mst_gen_customer
      JOIN mst_cust_masters ON mst_gen_customer.cust_seq = mst_cust_masters.cust_seq
    -------------------------------------------------------
 [bad]
 SELECT cust_seq  
      FROM mst_gen_customer, mst_cust_masters
     WHERE mst_gen_customer.cust_seq = mst_cust_masters.cust_Seq
 ```
 *  선택하기  
 --- 
 | 순번     | 개념        | 예시     |
 | :------------- | :------------- | :------------- |
 | 1       | full talbe 명칭 쓰기 | mst_cust_masters |
 | 2       | 의미있는 명칭으로 바꾸기(규칙 필요) | mst_cust_masters -> cust_master |  
 | 3       | 단순 알파벳 사용 |mst_cust_masters -> a |
 ---

* Line 정렬 규칙
 * 산자(+, -,  /, || ), 교연산자(=, !=, <, >, <=, >=, <> ) 앞뒤에 한 칸을 띄운다.
 *  선택하기(DML, SUB_QUERY)  
 ---
 | 순번     | 개념        | 예시     |
 | :------------- | :------------- | :------------- |
 | 1       | DML 라인 왼쪽 정렬 |  |
 | 2       | DML 라인 오른쪽 정렬 | |
---

 *  선택하기(들여쓰기)  
 ---
 | 순번     | 개념        | 예시     |
 | :------------- | :------------- | :------------- |
 | 1       | 띄어쓰기 ?칸 |  |
 | 2       | TAB사용 | |  
---



[참조 GitLab](https://about.gitlab.com/handbook/business-ops/data-team/sql-style-guide/#use-ctes-common-table-expressions-not-subqueries)  

[참조 Naver](https://m.blog.naver.com/PostView.nhn?blogId=holyruby&logNo=40061580024&proxyReferer=https%3A%2F%2Fwww.google.com%2F)

[참조 DB가이드](http://www.dbguide.net/db.db?cmd=view&boardUid=148198&boardConfigUid=9&boardIdx=135&boardStep=1)
