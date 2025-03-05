
### 문제 
![KakaoTalk_20250305_160159532](https://github.com/user-attachments/assets/1570ee72-8a27-4b2b-b2dd-22931d5dceb7)

이거 왜 내가 틀렸는지 이해가 안돼
---

### 풀이

주어진 SQL 쿼리는 **RIGHT OUTER JOIN**을 사용하여 두 테이블 `SAMPLE1`과 `SAMPLE2`를 조인합니다. 쿼리의 조건은 다음과 같습니다:

```sql
SELECT *
FROM SAMPLE1 A
RIGHT OUTER JOIN SAMPLE2 B
ON (A.COL1 = B.COL1 AND B.COL2 IS NOT NULL);
```


#### 1. **RIGHT OUTER JOIN**

- **RIGHT OUTER JOIN**은 오른쪽 테이블(`SAMPLE2`)의 모든 행을 유지하고, 왼쪽 테이블(`SAMPLE1`)에서 조건에 맞는 데이터를 가져옵니다.
- 조건에 맞지 않는 경우, 왼쪽 테이블의 값은 `NULL`로 채워집니다.


#### 2. **ON 절**

- `ON` 절은 두 테이블을 조인할 때 사용할 조건을 정의합니다.
- 여기서는 두 조건이 있습니다:
    - `A.COL1 = B.COL1`: 두 테이블의 `COL1` 값이 동일한 행만 조인합니다.
    - `B.COL2 IS NOT NULL`: 오른쪽 테이블(`SAMPLE2`)의 `COL2` 값이 `NULL`이 아닌 행만 포함합니다.


#### 3. 테이블 데이터 분석

테이블 데이터를 기준으로 조인을 수행하면 다음과 같은 결과가 나옵니다:

##### SAMPLE1 테이블

| COL1 | COL2 |
| :-- | :-- |
| 2 | G |
| 3 | H |
| 3 | I |

##### SAMPLE2 테이블

| COL1 | COL2 |
| :-- | :-- |
| 1 | A |
| 2 | B |
| 3 | NULL |
| 4 | D |
| 5 | E |

#### 4. 조인 과정 설명

**조인 조건:**

- 첫 번째 조건: `A.COL1 = B.COL1`
- 두 번째 조건: `B.COL2 IS NOT NULL`

**조인 결과:**

- `B.COL2 IS NULL`인 행은 제외됩니다 (`COL1=3, COL2=NULL`).
- 오른쪽 테이블(SAMPLE2)의 모든 행이 유지되며, 왼쪽 테이블(SAMPLE1)의 데이터는 조건에 따라 매칭됩니다.


##### 결과 데이터

| A.COL1 | A.COL2 | B.COL1 | B.COL2 |
| :-- | :-- | :-- | :-- |
| NULL | NULL | 1 | A |
| 2 | G | 2 | B |
| NULL | NULL | 4 | D |
| NULL | NULL | 5 | E |

#### 최종 결과 설명

위 결과는 오른쪽 테이블(SAMPLE2)의 모든 행을 유지하면서, 왼쪽 테이블(SAMPLE1)의 데이터를 조건에 따라 매칭한 것입니다.

---

### ON 절과 WHERE 절 차이점

#### **ON 절**

- 조인 시 두 테이블 간에 매칭되는 행을 필터링하는 역할을 합니다.
- 조인 과정에서 조건을 적용하며, 조인된 결과에 영향을 줍니다.


#### **WHERE 절**

- 조인이 끝난 후 최종 결과에서 추가적인 필터링을 수행합니다.
- WHERE 절은 조인된 결과를 기준으로 데이터를 제한합니다.

예를 들어:

```sql
SELECT *
FROM SAMPLE1 A
RIGHT OUTER JOIN SAMPLE2 B
ON (A.COL1 = B.COL1)
WHERE B.COL2 IS NOT NULL;
```

위 쿼리는 먼저 모든 데이터를 RIGHT OUTER JOIN으로 조인한 후, 최종적으로 `B.COL2 IS NOT NULL` 조건을 적용하여 결과를 필터링합니다.

<div style="text-align: center">⁂</div>

[^1]: https://pplx-res.cloudinary.com/image/upload/v1741158189/user_uploads/PwSixfGPgawpTTT/KakaoTalk_20250305_160159532.jpg

