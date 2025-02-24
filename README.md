### 📂 **SQLCuriosityLog**  
📚 **SQL 공부 중 생긴 질문과 답변을 정리한 저장소**  

**SQLCuriosityLog**에 오신 것을 환영합니다!  
이 저장소는 SQL을 공부하면서 생긴 질문들을 기록하고, 그에 대한 답변을 정리한 Q&A 형식의 자료입니다. 기초적인 내용부터 고급 주제까지, SQL의 "왜?"와 "어떻게?"를 탐구하는 데 도움이 될 것입니다.  

---

## 🌟 목적  

이 저장소는 다음을 목표로 합니다:  
1. SQL에 대한 **질문과 답변 모음**을 제공합니다.  
2. 학습 과정을 기록하고 이해를 심화시킬 수 있는 **개인 학습 로그**로 활용됩니다.  
3. 비슷한 궁금증을 가진 사람들에게 **도움이 되는 자료**를 제공합니다.  

---

## 🛠️ 사용 방법  

1. **질문 탐색하기**  
   질문은 카테고리별로 나누어져 있습니다. 각 질문에는 상세한 설명과 필요한 경우 참고 자료가 포함되어 있습니다.  

2. **기여하기**  
   새로운 질문이나 답변을 추가하고 싶으신가요? Pull Request를 통해 자유롭게 기여할 수 있습니다. 함께 성장하는 지식의 장을 만들어 봅시다!  

---

## 🗂️ 예상 되는 내용들  

1. **핵심 개념**  
   - `JOIN`과 `UNION`의 차이는 무엇인가요?  
   - `PRIMARY KEY`와 `FOREIGN KEY`의 차이점은?  
   - 인덱스(Index)는 어떻게 동작하나요?  

2. **고급 주제**  
   - 서브쿼리 vs 조인의 성능 차이는?  
   - 트랜잭션과 격리 수준(Isolation Level)의 개념  
   - 뷰(View)와 테이블(Table)의 차이점  

3. **추가 주제**  
   - SQL에서 성능 최적화하는 방법은?  
   - 정규화(Normalization)와 비정규화(Denormalization)의 차이점  

---

## 🤝 기여 방법  

이 저장소에 기여하고 싶다면 다음을 참고하세요:  
1. **질문 제출하기**  
   새로운 SQL 관련 질문을 Issue로 남겨주세요.  
2. **답변 추가하기**  
   기존의 질문에 대한 답변을 개선하거나, 새로운 답변을 추가해주세요.  
3. **저장소 개선하기**  
   카테고리 분류, 태그 추가, 검색 기능 등 새로운 아이디어를 제안하고 구현해주세요.  

---

## 📝 예시 Q&A  

### Q: **`JOIN`과 `UNION`의 차이는 무엇인가요?**  
**A:**  
- `JOIN`은 여러 테이블을 결합하여 **열(column) 기준**으로 데이터를 조회합니다.  
- `UNION`은 여러 `SELECT` 결과를 **행(row) 기준**으로 합칩니다.  

   ```sql
   -- JOIN 예제: 두 테이블을 결합하여 특정 데이터를 조회
   SELECT employees.name, departments.department_name  
   FROM employees  
   JOIN departments ON employees.department_id = departments.id;  

   -- UNION 예제: 두 개의 SELECT 결과를 하나로 합침
   SELECT name FROM employees  
   UNION  
   SELECT name FROM customers;  
   ```  

---

## 📌 라이선스  

이 저장소는 [MIT 라이선스](LICENSE)에 따라 사용됩니다.  
