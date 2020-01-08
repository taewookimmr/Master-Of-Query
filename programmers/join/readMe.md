![Join](./join.png)

### 1.천재지변으로 인해 일부 데이터가 유실되었습니다. 입양을 간 기록은 있는데, 보호소에 들어온 기록이 없는 동물의 ID와 이름을 ID 순으로 조회하는 SQL문을 작성해주세요.

```sql
SELECT O.ANIMAL_ID, O.NAME
    FROM ANIMAL_OUTS O
    LEFT JOIN ANIMAL_INS I ON O.ANIMAL_ID = I.ANIMAL_ID
    WHERE I.ANIMAL_ID IS NULL
    ORDER BY O.ANIMAL_ID
```

### 2. 관리자의 실수로 일부 동물의 입양일이 잘못 입력되었습니다. 보호 시작일보다 입양일이 더 빠른 동물의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일이 빠른 순으로 조회해야합니다.

```sql
select i.animal_id, i.name
    from animal_ins i
    left join animal_outs o on i.animal_id = o.animal_id
    where i.datetime > o.datetime
    order by i.datetime
```

### 3. 아직 입양을 못 간 동물 중, 가장 오래 보호소에 있었던 동물 3마리의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일 순으로 조회해야 합니다.

```sql
SELECT i.name, i.datetime 
    from animal_ins i 
    left join animal_outs o 
    on i.animal_id = o.animal_id
    where o.animal_id is null
    order by i.datetime
    limit 3;
```

### 4. 보호소에서 중성화 수술을 거친 동물 정보를 알아보려 합니다. 보호소에 들어올 당시에는 중성화1되지 않았지만, 보호소를 나갈 당시에는 중성화된 동물의 아이디와 생물 종, 이름을 조회하는 아이디 순으로 조회하는 SQL 문을 작성해주세요.

```sql
SELECT i.animal_id, i.animal_type, i.name 
    from animal_ins i
    join animal_outs o
    on i.animal_id = o.animal_id
    where i.sex_upon_intake != sex_upon_outcome
    order by i.animal_id;
```