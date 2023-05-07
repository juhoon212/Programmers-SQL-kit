# Programmers SQL KIT

프로그래머스 sql 고득점 kit 문제풀이용 레포지토리입니다. 



![스크린샷 2023-05-07 오후 4 40 29](https://user-images.githubusercontent.com/121741140/236664521-013667c4-f489-416f-86a2-0c0e1ef1d7ed.png)
- 2023년 5월 7일 시작

## SELECT

### 3월에 태어난 여성 회원 목록 출력하기

```
SELECT
    member_id,
    member_name,
    gender,
    to_char(DATE_OF_BIRTH, 'YYYY-MM-DD')as date_of_birth
from
    member_profile
WHERE
    TO_CHAR(DATE_OF_BIRTH, 'MM') = '03' and
    tlno is not null AND GENDER = 'W'
order by
    member_id asc
 ```

### 모든 레코드 조회하기

```
SELECT *
FROM ANIMAL_INS
ORDER BY ANIMAL_ID
```

