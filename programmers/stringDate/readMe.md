### 1. 동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별을 조회하는 SQL 문을 작성해주세요

```sql
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE
    FROM ANIMAL_INS
    WHERE NAME IN ('Lucy','Ella','Pickle','Rogan','Sabrina','Mitty')
```

### 2.  동물 보호소에 들어온 동물 이름 중, 이름에 EL이 들어가는 개의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 이름 순으로 조회해주세요. 단, 이름의 대소문자는 구분하지 않습니다.

```sql
SELECT  A.ANIMAL_ID, A.NAME
    FROM    ANIMAL_INS AS A
    WHERE   A.ANIMAL_TYPE   =   'Dog'
        AND     A.NAME  LIKE '%el%'
    ORDER BY A.NAME
```


### 3.  중성화된 동물은 SEX_UPON_INTAKE 컬럼에 'Neutered' 또는 'Spayed'라는 단어가 들어있습니다. 동물의 아이디와 이름, 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 중성화가 되어있다면 'O', 아니라면 'X'라고 표시해주세요.

```sql
SELECT  A.ANIMAL_ID
    ,   A.NAME
    ,   CASE    WHEN A.SEX_UPON_INTAKE  REGEXP 'Neutered|Spayed'
                THEN 'O'
                ELSE 'X'
        END AS 중성화
FROM   ANIMAL_INS AS A 
ORDER BY A.ANIMAL_ID
```


### 4. 입양을 간 동물 중, 보호 기간이 가장 길었던 동물 두 마리의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 기간이 긴 순으로 조회해야 합니다.

```sql
SELECT o.animal_id, o.name 
    from animal_outs o
    left join animal_ins i on o.animal_id = i.animal_id
    order by (o.datetime-i.datetime) desc
    limit 2;
```


### 5. ANIMAL_INS 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜를 조회하는 SQL문을 작성해주세요. 이때 결과는 아이디 순으로 조회해야 합니다.

```sql
SELECT
    ANIMAL_ID, NAME, DATE_FORMAT(DATETIME,'%Y-%m-%d') AS '날짜'
FROM
    ANIMAL_INS
;
```

