## 1. 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이가 개보다 먼저 조회해주세요.

```sql
SELECT ANIMAL_TYPE, COUNT(*) AS 'COUNT'
    FROM ANIMAL_INS
    GROUP BY ANIMAL_TYPE
    ORDER BY ANIMAL_TYPE;
```

## 2. 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.

```sql
SELECT NAME, COUNT(*) as 'COUNT'
    FROM ANIMAL_INS
    GROUP BY NAME HAVING COUNT(NAME)>1
    ORDER BY NAME
```

## 3. 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 9시부터 19시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

```sql
SELECT HOUR(DATETIME) AS 'HOUR',
    count(HOUR(DATETIME)) AS 'COUNT'
        FROM ANIMAL_OUTS
        GROUP BY HOUR(DATATIME)
        HAVING hour >= 9 AND hour <= 19
        ORDER BY HOUR(DATETIME)
```


## 4. 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

```sql
set @hour = -1;
select 
    (@hour := @hour +1) as 'HOUR',
    (select count(*) from animal_outs where HOUR(DATETIME) = @hour) as 'COUNT'
    from animal_outs 
where @hour < 23
```