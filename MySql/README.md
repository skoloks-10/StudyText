# 🗄️ MySQL 학습 기록

> 관계형 데이터베이스(RDBMS)의 핵심 SQL을 체계적으로 학습하는 과정입니다.

## 📖 학습 로드맵

### 📊 데이터 조회 기초 (001강)
- **001. SELECT 전반기능, 각종 연산자**
  - 모든 컬럼 조회 (`SELECT *`)
  - 특정 컬럼만 조회
  - WHERE를 이용한 행 필터링
  - 산술, 비교, 논리 연산자 활용
  - LIKE, IN, BETWEEN 등 다양한 조건

### 🔧 함수 활용 (002강)
- **002. 함수**
  - 문자열 함수 (CONCAT, SUBSTRING, UPPER, LOWER, TRIM 등)
  - 숫자 함수 (ROUND, ABS, CEILING, FLOOR 등)
  - 날짜 함수 (NOW(), DATE_ADD(), DATE_DIFF() 등)
  - 집계 함수 (COUNT, SUM, AVG, MIN, MAX)
  - GROUP BY, HAVING을 이용한 그룹화

### 🔗 고급 쿼리 (003강)
- **003. 서브쿼리, JOIN, UNION**
  - 서브쿼리 (Sub Query) - SELECT 안의 SELECT
  - INNER JOIN - 두 테이블의 교집합
  - LEFT/RIGHT/FULL OUTER JOIN - 부분/전체 일치
  - CROSS JOIN - 카르테시안 곱
  - UNION - 두 쿼리 결과 합치기
  - UNION ALL - 중복 포함하여 합치기

### 🏗️ 테이블과 데이터 조작 (004강)
- **004. 테이블 생성, 데이터 조작, 자료형**
  - CREATE TABLE - 테이블 설계 및 생성
  - 데이터 타입 (INT, VARCHAR, TEXT, DATE, BOOLEAN 등)
  - 제약조건 (PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, DEFAULT)
  - INSERT - 데이터 추가
  - UPDATE - 데이터 수정
  - DELETE - 데이터 삭제
  - DROP TABLE - 테이블 삭제

---

## 🎯 SQL 문법 정리

| 분류 | 명령어 | 용도 |
|------|--------|------|
| **DQL** | SELECT | 데이터 조회 |
| **DML** | INSERT, UPDATE, DELETE | 데이터 조작 |
| **DDL** | CREATE, ALTER, DROP | 테이블/스키마 관리 |
| **DCL** | GRANT, REVOKE | 권한 관리 |

---

## 💡 자주 사용하는 SQL 패턴

```sql
-- 1. 기본 SELECT
SELECT * FROM Customers;
SELECT CustomerName, Country FROM Customers;

-- 2. 조건문으로 필터링
SELECT * FROM Customers WHERE Country = 'Korea';
SELECT * FROM Orders WHERE Amount > 100 AND Status = 'Completed';

-- 3. LIKE를 이용한 검색
SELECT * FROM Customers WHERE CustomerName LIKE '%John%';

-- 4. 정렬 및 제한
SELECT * FROM Customers ORDER BY CustomerName ASC LIMIT 10;

-- 5. 그룹화 및 집계
SELECT Country, COUNT(*) as customer_count
FROM Customers
GROUP BY Country
HAVING COUNT(*) > 5;

-- 6. JOIN - 두 테이블 연결
SELECT c.CustomerName, o.OrderID, o.Amount
FROM Customers c
INNER JOIN Orders o ON c.CustomerID = o.CustomerID;

-- 7. 서브쿼리
SELECT * FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders WHERE Amount > 1000);

-- 8. UNION - 두 쿼리 결과 합치기
SELECT CustomerName as Name FROM Customers
UNION
SELECT EmployeeName as Name FROM Employees;

-- 9. 데이터 추가
INSERT INTO Customers (CustomerName, Country)
VALUES ('John Doe', 'Korea');

-- 10. 데이터 수정
UPDATE Customers
SET Country = 'USA'
WHERE CustomerID = 1;

-- 11. 데이터 삭제
DELETE FROM Customers WHERE CustomerID = 1;

-- 12. 테이블 생성
CREATE TABLE Users (
  UserID INT PRIMARY KEY AUTO_INCREMENT,
  Username VARCHAR(50) NOT NULL UNIQUE,
  Email VARCHAR(100),
  CreatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  IsActive BOOLEAN DEFAULT TRUE
);

-- 13. 날짜 함수
SELECT * FROM Orders
WHERE OrderDate BETWEEN '2024-01-01' AND '2024-12-31';

SELECT CustomerName, DATEDIFF(NOW(), CreatedAt) as days_since_signup
FROM Customers;

-- 14. 문자열 함수
SELECT CONCAT(FirstName, ' ', LastName) as FullName FROM Users;
SELECT SUBSTRING(Email, 1, 5) as EmailPrefix FROM Users;
```

---

## 🏢 데이터베이스 설계 기초

### 1. 정규화 (Normalization)
- **1NF**: 원자성 (각 속성은 단일 값만 가짐)
- **2NF**: 부분 함수 종속 제거 (모든 비키 속성이 전체 키에 의존)
- **3NF**: 이행적 함수 종속 제거 (비키 속성이 다른 비키 속성에 의존하지 않음)

### 2. 관계 설계
```sql
-- 일대다 관계 (1:N)
CREATE TABLE Authors (
  AuthorID INT PRIMARY KEY,
  AuthorName VARCHAR(100)
);

CREATE TABLE Books (
  BookID INT PRIMARY KEY,
  BookTitle VARCHAR(100),
  AuthorID INT,
  FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID)
);

-- 다대다 관계 (M:N) - 중간 테이블 필요
CREATE TABLE StudentCourses (
  StudentID INT,
  CourseID INT,
  Enrollment_Date DATE,
  PRIMARY KEY (StudentID, CourseID),
  FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
  FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

---

## 🛠️ 데이터베이스 도구

### 온라인 학습 플랫폼
- **W3Schools SQL Playground**: https://www.w3schools.com/mysql/trymysql.asp
- 기본 데이터베이스(Customers, Orders, Products 등) 제공
- 샘플 쿼리로 즉시 실습 가능

### 로컬 환경
```bash
# MySQL 설치
# Windows: https://dev.mysql.com/downloads/mysql/

# 로컬 서버 시작
mysql -u root -p

# 데이터베이스 생성
CREATE DATABASE mydb;
USE mydb;

# 테이블 생성 및 쿼리 실행
# .sql 파일 import 또는 쿼리 입력
```

---

## 📚 학습 방법

1. **온라인 플랫폼 먼저**: W3Schools에서 기본 개념과 샘플 데이터로 실습
2. **순차 학습**: 001강부터 차례대로 진행
3. **SQL 문법 숙달**: 각 강의마다 기본 예제 작성
4. **실전 데이터베이스 설계**: 004강에서 자신의 프로젝트 구조 직접 설계
5. **복습**:
   - 1주일 후: 어려웠던 JOIN, 서브쿼리 복습
   - 1달 후: 전체 SQL 명령어 복습

---

## 🎓 다음 단계

- **PHP/Node.js와 연동**: 웹 애플리케이션에서 데이터베이스 활용
- **쿼리 최적화**: 인덱스, 실행 계획 분석
- **트랜잭션과 잠금**: 동시성 제어
- **관계형 데이터베이스 설계 심화**: 정규화, 성능 최적화

---

## 📖 참고 자료

- MySQL 공식 문서: https://dev.mysql.com/doc/
- W3Schools SQL Tutorial: https://www.w3schools.com/sql/
- SQL 최적화 가이드: https://use-the-index-luke.com/

---

**마지막 업데이트**: 2026-02-26

