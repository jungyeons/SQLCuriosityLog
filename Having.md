# Q.집계 함수에서 HAVING 절에서만 집계함수를 사용할 수 있는 이유?

A.SQL을 사용하다 보면 데이터를 그룹화하여 분석할 일이 많습니다. 이때 `GROUP BY`와 함께 집계 함수(예: `COUNT`, `SUM`, `AVG`, `MAX`, `MIN` 등)를 사용하여 데이터를 요약할 수 있습니다. 하지만 특정 조건을 적용할 때 `WHERE`가 아니라 `HAVING`을 사용해야 하는 경우가 있습니다. 이번 글에서는 그 이유를 예제와 함께 설명하겠습니다.

## 1. WHERE와 HAVING의 차이

- **WHERE**: 집계를 수행하기 전에 각 개별 행에 대한 필터링을 수행합니다.
- **HAVING**: 집계가 수행된 후 그룹화된 결과에 대해 필터링을 수행합니다.

즉, WHERE 절은 개별 행을 대상으로 조건을 적용하고, HAVING 절은 그룹화된 결과(집계 함수 결과)에 조건을 적용할 때 사용됩니다.

## 2. 예제: WHERE와 HAVING 비교

다음과 같은 테이블 `sales`가 있다고 가정해 보겠습니다.

| id | product  | category  | amount |
|----|---------|----------|--------|
| 1  | A       | Food     | 100    |
| 2  | B       | Food     | 200    |
| 3  | C       | Drink    | 150    |
| 4  | D       | Drink    | 250    |
| 5  | E       | Food     | 300    |

### (1) WHERE 절 사용 예시

예를 들어, `amount`가 200 이상인 데이터만 조회한다고 가정하면 WHERE 절을 사용할 수 있습니다.

```sql
SELECT * FROM sales WHERE amount >= 200;
```

출력 결과:

| id | product | category | amount |
|----|---------|----------|--------|
| 2  | B       | Food     | 200    |
| 4  | D       | Drink    | 250    |
| 5  | E       | Food     | 300    |

여기서는 각 개별 행의 `amount` 값이 200 이상인 경우만 필터링되었습니다.

### (2) HAVING 절 사용 예시

이번에는 카테고리별로 총 판매 금액을 구한 후, 총 판매 금액이 300 이상인 카테고리만 조회하려고 합니다.

```sql
SELECT category, SUM(amount) AS total_amount
FROM sales
GROUP BY category
HAVING SUM(amount) >= 300;
```

출력 결과:

| category | total_amount |
|----------|-------------|
| Food     | 600         |
| Drink    | 400         |

여기서 중요한 점은 `SUM(amount) >= 300` 조건이 개별 행이 아니라 그룹화된 결과에 적용되었다는 것입니다. 만약 `WHERE SUM(amount) >= 300`을 사용하려 하면 오류가 발생합니다. 왜냐하면 `WHERE`는 개별 행에 대해 작동하므로, 집계 함수 결과를 필터링할 수 없기 때문입니다.

## 3. 정리

- `WHERE` 절은 개별 행을 필터링할 때 사용합니다.
- `HAVING` 절은 집계된 결과를 필터링할 때 사용합니다.
- `HAVING`은 `GROUP BY`와 함께 사용되며, 집계 함수(`SUM`, `COUNT`, `AVG`, 등)의 결과에 조건을 적용할 때 필요합니다.

### 💡 기억할 점
집계 함수의 결과를 필터링할 때는 반드시 `HAVING` 절을 사용해야 합니다!

이해를 돕기 위해 간단한 예제와 함께 설명해 보았는데요, 도움이 되셨길 바랍니다! 😊

