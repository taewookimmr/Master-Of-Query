# Setting Postgresql on Mac

## 1. homebrew를 사용한 설치

* brew search postgresql
* brew install postgresql
* postgres --version // 버전 확인

## 2. Postgresql 서비스 시작

* postgres -D /usr/local/var/postgres

## 3. 기본 명령어

```sql
CREATE USER kirk 1111; // 이름이 kirk, 비밀번호가 1111인 유저 생성
CREATE DATABASE space kirk; // 이름이 space, 소유주가 kirk인 데이터베이스 생성
CREATE TABLE animal_ins (
    animal_id varchar(30) not null,
    animal_type varchar(30) not null,
    datetime datetimme not null,
    intake_condition varchar(30) not null,
    name varchar(30),
    sex_uopn_intake varchar(30) not null,
);
```




