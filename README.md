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
### 12세 이하인 여자 환자 목록 출력하기

```
SELECT PT_NAME, PT_NO, GEND_CD, AGE , NVL(TLNO, 'NONE')
FROM PATIENT
WHERE AGE <= 12 AND GEND_CD = 'W'
ORDER BY AGE DESC, PT_NAME;
```

### 과일로 만든 아이스크림 고르기

```
SELECT F.FLAVOR 
FROM FIRST_HALF F JOIN ICECREAM_INFO I ON F.FLAVOR = I.FLAVOR
WHERE I.INGREDIENT_TYPE = 'fruit_based' AND
F.TOTAL_ORDER > 3000
ORDER BY F.TOTAL_ORDER DESC;
```

### 재구매가 일어난 상품과 회원 리스트 구하기
```
SELECT USER_ID, PRODUCT_ID
FROM (
    SELECT USER_ID, PRODUCT_ID, COUNT(*) C
      FROM ONLINE_SALE
      GROUP BY USER_ID , PRODUCT_ID) OS
WHERE C > 1
ORDER BY USER_ID, PRODUCT_ID DESC;
```

### 서울에 위치한 식당 목록 출력하기

```
SELECT RI.REST_ID,
       RI.REST_NAME,
       RI.FOOD_TYPE,
       RI.FAVORITES,
       RI.ADDRESS,
       ROUND(AVG(REVIEW_SCORE),2) AS AVG_REVIEW
FROM REST_INFO RI JOIN REST_REVIEW RR ON RI.REST_ID = RR.REST_ID
WHERE RI.ADDRESS LIKE '서울%'
GROUP BY RI.REST_ID, RI.REST_NAME, RI.FOOD_TYPE, RI.FAVORITES, RI.ADDRESS
ORDER BY AVG_REVIEW DESC, RI.FAVORITES DESC; 
```

### 조건에 부합하는 중고거래 댓글 조회하기

```
SELECT UGB.TITLE,
        UGB.BOARD_ID,
        UGR.REPLY_ID,
        UGR.WRITER_ID,
        UGR.CONTENTS,
        TO_CHAR(UGR.CREATED_DATE,'YYYY-MM-DD') AS C_DATE
FROM USED_GOODS_BOARD UGB JOIN USED_GOODS_REPLY UGR ON UGB.BOARD_ID = UGR.BOARD_ID
WHERE TO_CHAR(UGB.CREATED_DATE, 'YYYY-MM') = '2022-10'
ORDER BY C_DATE, UGB.TITLE; // 일반 조인은 메인이 되는 왼쪽 테이블 기준으로 조인된다
```
### 조건에 맞는 도서와 저자 리스트 출력하기

```
SELECT B.BOOK_ID, A.AUTHOR_NAME, TO_CHAR(B.PUBLISHED_DATE, 'YYYY-MM-DD') PD
FROM BOOK B JOIN AUTHOR A ON B.AUTHOR_ID = A.AUTHOR_ID
WHERE CATEGORY = '경제'
ORDER BY PD;
```
