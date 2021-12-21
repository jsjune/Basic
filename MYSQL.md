# 데이터베이스

- 데이터베이스 생성
	```
	mysql> CREATE DATABASE dbname;
	```
- 데이터베이스 목록 보기
	```
	mysql> SHOW DATABASES;
	```  
- dbname 데이터베이스 사용 시  
	```
	mysql> USE dbname;
	```  
- dbname 데이터베이스 삭제  
	```
	mysql> DROP DATABASE [IF EXISTS] dbname
	```  
- 테이블을 생성할 데이터베이스를 먼저 사용하겠다고 명령한 후에,  
	```
	mysql> CREATE DATABASE dave;  
	mysql> use dave;
	```   

# 테이블

- 테이블 생성  
	```
	mysql> CREATE TABLE 테이블명 (  
 		컬럼명 데이터형,  
		컬러명 데이터형,  
 			.  
			.  
 		Primary Key() 가 될 필드 지정  
		);
	```

- 테이블 조회  
	```
	mysql> SHOW TABLES;
	```  

- 테이블 삭제  
	```
	mysql> DROP TABLE [IF EXISTS] 테이블명;
	```  

- 테이블 구조 수정  
	- 테이블에 새로운 컬럼추가  
		문법: ALTER TABLE [테이블명] ADD COLUMN [추가할 컬럼명][추가할 컬럼 데이터형]   
		```
		mysql> ALTER TABLE mytable ADD COLUMN model_type varchar(10) NOT NULL;
		```  

	- 테이블 컬럼 타입 변경  
		문법: ALTER TABLE [테이블명] MODIFY COLUMN [변경할 컬럼명][변경할 컬럼 타입]  
		```
		mysql>ALTER TABLE mytable MODIFY COLUMN name varchar(20) NOT NULL;
		```   

	- 테이블 컬럼 이름 변경  
		문법: ALTER TABLE [테이블명] CHANGE COLUMN [기존 컬럼 명][변경할 컬럼 명][변경할 컬럼 타입]  
		```
		mysql>ALTER TABLE mytable CHANGE COLUMN modelnumber model_num varchar(10) NOT NULL;
		```  

	- 테이블 컬럼 삭제  
		문법: ALTER TABLE [테이블명] DROP COLUMN [삭제할 컬럼 명]  
		```
		mysql>ALTER TABLE mytable DROP COLUMN series;
		```  
# 데이터
- 데이터 생성  
	- 테이블 전체 컬럼에 대응하는 값을 모두 넣기  
		```  
		mysql> INSERT INTO 테이블명 VALUES(값1, 값2, ...);  
		```  
	- 테이블 특정 컬럼에 대응하는 값만 넣기 (지정되지 않은 컬럼은 디폴트값 또는 NULL값이 들어감)  
		```  
		mysql> INSERT INTO 테이블명 (col1, col2, ...) VALUES(값1, 값2, ...);  
		``` 

- 데이터 읽기(검색)  
	- 테이블 전체 컬럼의 데이터 모두 읽기  
		```
		mysql> SELECT * FROM 테이블명;
		```  
	- 테이블 특정 컬럼의 데이터만 읽기  
		```
		mysql> SELECT 컬럼1, 컬럼2, ... FROM 테이블명;  
		mysql> SELECT name, model_num FROM mytable;
		```  
	- 테이블 특정 컬럼의 데이터를 검색하되, 표시할 컬럼명도 다르게 하기  
		```
		mysql> SELECT 컬럼1 AS 바꿀컬럼이름, 컬럼2 AS 바꿀컬럼이름 FROM 테이블명;
		```  
	- 데이터 정렬해서 읽기  
	       - DESC는 내림차순 ASC는 오름차순  
		```
		mysql> SELECT * FROM 테이블명 ORDER BY 정렬할기준컬럼명 DESC;  
		mysql> SELECT 컬럼1, 컬럼2 FROM 테이블명 ORDER BY 정렬할기준컬럼명 ASC;
		```  
	- 조건에 맞는 데이터만 검색하기 (비교)  
		- 예) WHERE 컬럼명 < 값  
		- 예) WHERE 컬럼명 > 값  
		- 예) WHERE 컬럼명 = 값  
			```
			SELECT * FROM 테이블명 WHERE 필드명 = '값'
			``` 
	- 조건에 맞는 데이터만 검색하기 (논리 연산자)  
                    - WHERE 조건문 으로 조건 검색  
		- 예) WHERE 컬럼명 < 값 OR 컬럼명 > 값  
		- 예) WHERE 컬럼명 > 값 AND 컬럼명 < 값  
			```
			SELECT * FROM 테이블명 WHERE (필드명='값') OR ( 필드명 ='값');     
			SELECT * FROM 테이블명 WHERE (필드명='값') AND ( 필드명 ='값');    
			``` 
	- 조건에 맞는 데이터만 검색하기 (LIKE 를 활용한 부분 일치)  
   	       -WHERE 조건문 으로 조건 검색  
		- 예) 홍으로 시작되는 값을 모두 찾을 경우  
			```
			SELECT * FROM 테이블명 WHERE 필드명 LIKE '홍%';  
			```  
		- 예) 홍이 들어간 값을 모두 찾을 경우  
			```
			SELECT * FROM 테이블명 WHERE 필드명 LIKE '%홍%';  
			```  
		- 예) 홍으로 시작되고 뒤에 2글자가 붙을 경우  
			```
			SELECT * FROM 테이블명 WHERE 필드명 LIKE '홍__';  
			SELECT * FROM 테이블명 WHERE 필드명 LIKE '홍%' AND 필드명='값'  
			``` 
	- 결과중 일부만 데이터 가져오기 (LIMIT 을 활용)  
		- 예) 결과중 처음부터 10개만 가져오기  
			```
			SELECT * FROM 필드명 LIMIT 10;  
			```  
		- 예) 결과중 100번째부터, 10개만 가져오기  
			```
			SELECT * FROM 필드명 LIMIT 100, 10;  
			```  
	- 조건 조합  
		- 위에서 나열한 조건을 조합해서 다양한 Query를 작성할 수 있음  
		- 조합 순서 SELECT FROM WHERE ORDER BY LIMIT  
		```
		예)  
			mysql> SELECT id, name FROM mytable  
			->  WHERE id < 4 AND name LIKE '%i%'  
			-> ORDER BY name DESC
			-> LIMIT 2;
		```	

- 데이터 수정  
	- 보통 WHERE 조건문과 함께 쓰여서, 특정한 조건에 맞는 데이터만 수정하는 경우가 많음  
		```
		mysql> UPDATE 테이블명 SET 수정하고 싶은 컬럼명 = '수정하고 싶은 값' WHERE 특정 컬럼 = '값';
		```  
	- 다수의 컬럼 값을 수정할 수도 있음  
		```
		mysql> UPDATE 테이블명 SET 수정하고 싶은 컬럼명1 = '수정하고 싶은 값',       
		수정하고 싶은 컬럼명2 = '수정하고 싶은 값',     	
		수정하고 싶은 컬럼명3 = '수정하고 싶은 값' WHERE 특정 컬럼 < '값';
		```  

- 데이터 삭제  
	- 보통 WHERE 조건문과 함께 쓰여서, 특정한 조건에 맞는 데이터만 삭제하는 경우가 많음  
		```
		mysql> DELETE FROM 테이블명 WHERE 특정 컬럼 = '값';
		```  
	- 테이블에 저장된 모든 데이터를 삭제할 수도 있음  
		```
		mysql> DELETE FROM 테이블명;
		```  







