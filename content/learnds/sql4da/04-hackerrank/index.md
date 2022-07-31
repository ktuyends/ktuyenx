---
title: "HackerRank"
weight: 4
subtitle: ""
excerpt: "Sau khi đã đi qua rất là nhiều kiến thức về SQL trong ba bài đầu tiên của _[Series - SQL for Data Analysis](/learnds/sql4da/)_, thì cũng đã đến lúc chúng ta bắt tay vào thực hành..."
slug: hackkerank
date: 2022-04-01
lastmod: 2022-04-01
draft: false
tags:
  - SQL
  - SQL for Data Analysis
---

## 1. Giới thiệu HackerRank

Sau khi đã đi qua rất là nhiều kiến thức về SQL trong ba bài đầu tiên của [Series - SQL for Data Analysis](/learnds/sql4da/), thì cũng đã đến lúc chúng ta bắt tay vào thực hành với một số ví dụ đơn giản ở trang [HackerRank](https://www.hackerrank.com/domains/sql). 

<p style="text-align:justify">Bài viết này là tổng hợp lời giải của mình về các câu hỏi ở HackerRank. Mình sẽ sử dụng hệ quản trị CSDL là SQL Server. Lưu ý là với mỗi DBMS, các hàm xử lý dữ liệu đôi khi sẽ không giống nhau. Một số hàm mình sử dụng:</p>

- `LEN()`: Số lượng các ký tự của một chuỗi.
- `LEFT()`: Lấy ra một số lượng các ký tự nhất định tính từ bên trái.
- `RIGHT()`: Lấy ra một số lượng các ký tự nhất định tính từ bên phải.
- `CONCAT()`: Hàm nối các chuỗi ký tự.
- `COUNT()`: Hàm đếm số lượng các record không NULL.
- `FORMAT(number, 'Fm'|'Nm')`: Định dạng số gồm m chữ số phần thập phân, trả về kiểu string.
- `ROUND(number, n)`: Làm tròn đến n chữ số thập phân.
- `CEILING(), FLOOR()`: Làm tròn đến số nguyên gần nhất.
- `CAST(column AS datatype)`: Chuyển đổi kiểu dữ liệu. 
- `TOP 50 PERCENT`: Lấy ra `50%` records.


## 2. Basic Select

<details>
<summary>
<b>1. Revising the Select Query I</b>
</summary>

```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'USA'
AND POPULATION > 100000;
```

</details>

<details>
<summary>
<b>2. Revising the Select Query II</b>
</summary>

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'USA'
AND POPULATION > 120000;
```

</details>

<details>
<summary>
<b>3. Select All</b>
</summary>

```sql
SELECT *
FROM CITY;
```

</details>

<details>
<summary>
<b>4. Select By ID</b>
</summary>

```sql
SELECT *
FROM CITY
WHERE ID = 1661;
```

</details>

<details>
<summary>
<b>5. Japanese Cities' Attributes</b>
</summary>

```sql
SELECT *
FROM CITY
WHERE CountryCode = 'JPN';
```

</details>

<details>
<summary>
<b>6. Japanese Cities' Names</b>
</summary>

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```
</details>

<details>
<summary>
<b>7. Weather Observation Station 1</b>
</summary>

```sql
SELECT CITY, STATE
FROM STATION;
```
</details>

<details>
<summary>
<b>8. Weather Observation Station 3</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
```
</details>

<details>
<summary>
<b>9. Weather Observation Station 4</b>
</summary>

```sql
SELECT COUNT(CITY) - COUNT (DISTINCT CITY)
FROM STATION;
```
</details>

<details>
<summary>
<b>10. Weather Observation Station 5</b>
</summary>

```sql
SELECT TOP 1 CITY, LEN(CITY)
FROM STATION
ORDER BY LEN(CITY), CITY;
UNION
SELECT TOP 1 CITY, LEN(CITY)
FROM STATION
ORDER BY LEN(CITY) DESC, CITY;
```
</details>

<details>
<summary>
<b>11. Weather Observation Station 6</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '[aeiou]%';
```
</details>

<details>
<summary>
<b>12. Weather Observation Station 7</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '%[aeiou]';
```
</details>

<details>
<summary>
<b>13. Weather Observation Station 8</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '[aeiou]%[aeiou]';
```
</details>

<details>
<summary>
<b>14. Weather Observation Station 9</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE '[aeiou]%';
```
</details>

<details>
<summary>
<b>15. Weather Observation Station 10</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE '%[aeiou]';
```
</details>

<details>
<summary>
<b>16. Weather Observation Station 11</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE '[aeiou]%[aeiou]';
```
</details>

<details>
<summary>
<b>17. Weather Observation Station 12</b>
</summary>

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '[^aeiou]%[^aeiou]';
```
</details>

<details>
<summary>
<b>18. Higher Than 75 Marks</b>
</summary>

```sql
SELECT NAME
FROM STUDENTS
WHERE MARKS > 75
ORDER BY RIGHT(NAME, 3), ID;
```
</details>

<details>
<summary>
<b>19. Employee Names</b>
</summary>

```sql
SELECT NAME
FROM EMPLOYEE
ORDER BY NAME;
```
</details>

<details>
<summary>
<b>20. Employee Salaries</b>
</summary>

```sql
SELECT NAME
FROM EMPLOYEE
WHERE SALARY > 2000 AND MONTHS < 10
ORDER BY EMPLOYEE_ID;
```
</details>

## 3. Advanced Select

<details>
<summary>
<b>21. Type of Triangle</b>
</summary>

```sql
SELECT CASE             
            WHEN A + B > C AND B + C > A AND A + C > B THEN
                CASE 
                    WHEN A = B AND B = C THEN 'Equilateral'
                    WHEN A = B OR B = C OR A = C THEN 'Isosceles'
                    ELSE 'Scalene'
                END
            ELSE 'Not A Triangle'
        END
FROM TRIANGLES;
```
</details>

<details>
<summary>
<b>22. The PADS</b>
</summary>

```sql
SELECT CONCAT(NAME, '(', LEFT(OCCUPATION, 1), ')')
FROM OCCUPATIONS
ORDER BY NAME;

SELECT CONCAT('There are a total of ', COUNT(OCCUPATION), ' ', LOWER(OCCUPATION), 's.')
FROM OCCUPATIONS
GROUP BY OCCUPATION
ORDER BY COUNT(OCCUPATION), OCCUPATION;
```
</details>

<details>
<summary>
<b>23. Occupations</b>
</summary>

```sql
SELECT Doctor
     , Professor
     , Singer
     , Actor
FROM (
SELECT 
    Row_Number() Over(Partition By Occupation Order by Name) AS row_no
  , Occupation
  , Name
FROM Occupations
) PivotData
PIVOT 
(
    Max(Name) For Occupation in ([Doctor], [Professor], [Singer], [Actor])
) PivotTable
```
</details>

<details>
<summary>
<b>24. Binary Tree Nodes</b>
</summary>

```sql
SELECT CASE
    WHEN P IS NULL THEN CONCAT(N, ' Root')
    WHEN N IN (SELECT DISTINCT P FROM BST) THEN CONCAT(N, ' Inner')
    ELSE CONCAT(N, ' Leaf')
    END
FROM BST
ORDER BY N ASC;
```
</details>

<details>
<summary>
<b>25. New Companies</b>
</summary>

```sql  
SELECT c.company_code
     , c.founder
     , COUNT(DISTINCT l.lead_manager_code)
     , COUNT(DISTINCT s.senior_manager_code)
     , COUNT(DISTINCT m.manager_code)
     , COUNT(DISTINCT e.employee_code) 
FROM Company c, Lead_Manager l, Senior_Manager s, Manager m, Employee e 
WHERE c.company_code = l.company_code 
    AND l.lead_manager_code=s.lead_manager_code 
    AND s.senior_manager_code=m.senior_manager_code 
    AND m.manager_code=e.manager_code 
GROUP BY c.company_code, c.founder
ORDER BY c.company_code;
```
</details>

## 4. Aggregation

<details>
<summary>
<b>26. Revising Aggregations - The Count Function</b>
</summary>

```sql
SELECT COUNT(NAME)
FROM CITY
WHERE POPULATION > 100000;
```
</details>

<details>
<summary>
<b>27. Revising Aggregations - The Sum Function</b>
</summary>

```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```
</details>

<details>
<summary>
<b>28. Revising Aggregations - Averages</b>
</summary>

```sql
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```
</details>

<details>
<summary>
<b>29. Average Population</b>
</summary>

```sql
SELECT ROUND(AVG(POPULATION), 0)
FROM CITY;  
```
</details>

<details>
<summary>
<b>30. Japan Population</b>
</summary>

```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```
</details>

<details>
<summary>
<b>31. Population Density Difference</b>
</summary>

```sql
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY;
```
</details>

<details>
<summary>
<b>32. The Blunder</b>
</summary>

```sql
SELECT CAST(CEILING(AVG(CAST(Salary AS Float)) - AVG(CAST(REPLACE(Salary, 0, '')AS Float))) AS INT)
FROM EMPLOYEES;
```
</details>

<details>
<summary>
<b>33. Top Earners</b>
</summary>

```sql
SELECT TOP 1 MAX(MONTHS * SALARY), COUNT(*)
FROM EMPLOYEE
GROUP BY MONTHS * SALARY
ORDER BY MONTHS * SALARY DESC;
```
</details>

<details>
<summary>
<b>34. Weather Observation Station 2</b>
</summary>

```sql
SELECT FORMAT(SUM(LAT_N), 'F2') AS lat, FORMAT(SUM(LONG_W), 'F2') AS lon
FROM STATION;
```
</details>

<details>
<summary>
<b>35. Weather Observation Station 13</b>
</summary>

```sql
SELECT FORMAT(SUM(LAT_N), 'F4')
FROM STATION
WHERE LAT_N > 38.7880 AND LAT_N < 137.2345;
```
</details>

<details>
<summary>
<b>36. Weather Observation Station 14</b>
</summary>

```sql
SELECT FORMAT(MAX(LAT_N), 'F4')
FROM STATION
WHERE LAT_N < 137.2345;
```
</details>

<details>
<summary>
<b>37. Weather Observation Station 15</b>
</summary>

```sql
SELECT FORMAT(LONG_W, 'F4')
FROM STATION
WHERE LAT_N = (SELECT MAX(LAT_N)
               FROM STATION
               WHERE LAT_N < 137.2345);
```
</details>

<details>
<summary>
<b>38. Weather Observation Station 16</b>
</summary>

```sql
SELECT FORMAT(MIN(LAT_N), 'F4')
FROM STATION
WHERE LAT_N > 38.7780;
```
</details>

<details>
<summary>
<b>39. Weather Observation Station 17</b>
</summary>

```sql
SELECT FORMAT(LONG_W, 'F4')
FROM STATION
WHERE LAT_N = (SELECT MIN(LAT_N)
               FROM STATION
               WHERE LAT_N > 38.7780);
```
</details>

<details>
<summary>
<b>40. Weather Observation Station 18</b>
</summary>

```sql
SELECT FORMAT(MAX(LAT_N) - MIN(LAT_N) + MAX(LONG_W) - MIN(LONG_W), 'F4')
FROM STATION;
```
</details>

<details>
<summary>
<b>41. Weather Observation Station 19</b>
</summary>

```sql
SELECT FORMAT(SQRT(POWER(MAX(LAT_N) - MIN(LAT_N) ,2) + POWER(MAX(LONG_W) - MIN(LONG_W) ,2)), 'F4')
FROM STATION;
```
</details>

<details>
<summary>
<b>42. Weather Observation Station 20</b>
</summary>

```sql
SELECT FORMAT((
    (SELECT MAX(LAT_N)
    FROM (
        SELECT TOP 50 PERCENT LAT_N
        FROM STATION
        ORDER BY LAT_N
    ) AS BotHalf)
    +
    (SELECT MIN(LAT_N)
    FROM (
        SELECT TOP 50 PERCENT LAT_N
        FROM STATION
        ORDER BY LAT_N DESC
    ) AS TopHafl)
) / 2, 'F4') AS MEDIAN
```
</details>


## 5. Basic Join

<details>
<summary>
<b>43. Population Census</b>
</summary>

```sql
SELECT SUM(CI.POPULATION)
FROM CITY CI 
JOIN COUNTRY CO ON CI.COUNTRYCODE = CO.CODE
WHERE CO.CONTINENT = 'ASIA';
```
</details>


<details>
<summary>
<b>44. African Cities</b>
</summary>

```sql
SELECT CI.NAME
FROM CITY CI 
JOIN COUNTRY CO ON CI.COUNTRYCODE = CO.CODE
WHERE CO.CONTINENT = 'AFRICA';
```
</details>

<details>
<summary>
<b>45. Average Population of Each Continent</b>
</summary>

```sql
SELECT CO.CONTINENT, FLOOR(AVG(CI.POPULATION))
FROM CITY CI 
JOIN COUNTRY CO ON CI.COUNTRYCODE = CO.CODE
GROUP BY CO.CONTINENT;
```
</details>

<details>
<summary>
<b>46. The Report</b>
</summary>

```sql
SELECT CASE WHEN GR.GRADE >= 8 THEN ST.NAME
       ELSE NULL END AS NAME, GR.GRADE, ST.MARKS
FROM STUDENTS ST 
JOIN GRADES GR ON ST.MARKS >= GR.MIN_MARK
               AND ST.MARKS <= GR.MAX_MARK
ORDER BY GR.GRADE DESC, ST.NAME;
```
</details>

<details>
<summary>
<b>47. Top Competitors</b>
</summary>

```sql
SELECT H.hacker_id, H.name
FROM Submissions S 
JOIN Challenges C ON S.challenge_id = C.challenge_id
JOIN Difficulty D ON C.difficulty_level = D.difficulty_level
JOIN Hackers H ON S.hacker_id = H.hacker_id
WHERE C.difficulty_level = D.difficulty_level AND S.Score = D.Score
GROUP BY H.hacker_id, H.name
HAVING COUNT(H.hacker_id) > 1
ORDER BY COUNT(H.hacker_id) DESC, H.hacker_id;
```
</details>

<details>
<summary>
<b>48. Ollivander's Inventory</b>
</summary>

**Phân tích bài toán:**

_Mục tiêu:_ Lựa chọn những cây đũa phép thuật non-evil mà có cặp _(power, age)_ có giá nhỏ nhất.

_Output:_ id, age _(secondary order in DESC)_, coins_needed, power _(primary order in DESC)_.  

```sql
--Bước 1: Xác định min coins
WITH Min_gold AS (
SELECT MIN(W.Coins_needed) OVER (PARTITION BY WP.age, W.power) AS min_coins
     , W.id
     , W.coins_needed
     , WP.age
     , W.power
FROM Wands W 
JOIN Wands_Property WP ON W.Code = WP.Code
WHERE WP.is_evil = 0)

-- Bước 2, xác định những coins_needed = min_coins
SELECT id
     , age
     , coins_needed
     , power
FROM Min_gold
WHERE coins_needed = min_coins
ORDER BY Power DESC, age DESC;
```
</details>

<details>
<summary>
<b>49. Challenges</b>
</summary>

```sql
-- Tính tổng challanges cho từng người
WITH data
AS
(
SELECT c.hacker_id as id, h.name as name, count(c.hacker_id) as counter
FROM Hackers h
JOIN Challenges c ON c.hacker_id = h.hacker_id
GROUP BY c.hacker_id, h.name
)

-- Kết quả
SELECT id, name, counter
FROM data
WHERE counter = (SELECT max(counter) FROM data) 
OR counter in (SELECT counter 
               FROM data
               GROUP BY counter
               HAVING count(counter) = 1 )
ORDER BY counter desc, id
```
</details>

<details>
<summary>
<b>50. Contest Leaderboard</b>
</summary>

```sql
-- Tạo bảng max score
WITH data AS 
(
SELECT H.hacker_id as id
     , H.name as name
     , S.challenge_id 
     , MAX(S.score) as max_score 
FROM Hackers H
JOIN Submissions S ON H.hacker_id = S.hacker_id
GROUP BY H.hacker_id, H.name, S.challenge_id
)

-- Kết quả
SELECT id, name, sum(max_score)
FROM data
GROUP BY id, name
HAVING sum(max_score) > 0
ORDER BY sum(max_score) DESC, id;
```
</details>

## 6. Advanced Join

<details>
<summary>
<b>51. SQL Project Planning</b>
</summary>

```sql
WITH Project_stat_date AS 
(
SELECT Start_date,
       RANK() OVER (ORDER BY Start_date) AS Rank_start
FROM Projects
WHERE Start_date NOT IN (SELECT End_date From Projects)
), 

Project_end_date AS 
(
SELECT End_date,
       RANK() OVER (ORDER BY End_date) AS Rank_end
FROM Projects
WHERE End_date NOT IN (SELECT Start_date From Projects)
)

SELECT Start_date
     , End_date
FROM Project_stat_date SD, Project_end_date ED
WHERE Rank_start = Rank_end
ORDER BY DATEDIFF(day, Start_date, End_date), Start_date;
```
</details>

<details>
<summary>
<b>52. Placements</b>
</summary>

```sql
-- student salary
WITH student_salary AS 
(
SELECT S.id AS id
     , S.name AS Name
     , P.salary As Salary
FROM Students S 
JOIN Packages P ON S.id = P.id
),

-- Friend salary
friends_salary AS 
(
SELECT F.id AS id
     , F.Friend_id AS Friend_id
     , P.salary AS Friend_salary
FROM Friends F 
JOIN Packages P ON F.Friend_id = P.id
)

-- Result
SELECT S.Name
FROM student_salary S
JOIN friends_salary F ON S.id = F.id
WHERE F.Friend_salary > S.Salary
ORDER BY F.Friend_salary
```
</details>


<details>
<summary>
<b>53. Symmetric Pairs</b>
</summary>

```sql
SELECT F1.X, F1.Y
FROM Functions F1 
JOIN Functions F2 ON F1.X = F2.Y and F1.Y = F2.X
GROUP BY F1.X, F1.Y
HAVING F1.X < F1.Y OR COUNT(F1.X) > 1
ORDER BY F1.X
```
</details>


<details>
<summary>
<b>54. Interviews</b>
</summary>

```sql
SELECT con.contest_id
     , con.hacker_id
     , con.name
     , SUM(total_submissions)
     , SUM(total_accepted_submissions)
     , SUM(total_views)
     , SUM(total_unique_views)
FROM contests con 
JOIN colleges col ON con.contest_id = col.contest_id 
JOIN challenges cha ON  col.college_id = cha.college_id 
LEFT JOIN
        (SELECT challenge_id
              , SUM(total_views) AS total_views
              , SUM(total_unique_views) AS total_unique_views
         FROM view_stats 
         GROUP BY challenge_id) vs ON cha.challenge_id = vs.challenge_id 
LEFT JOIN
       (SELECT challenge_id
             , SUM(total_submissions) AS total_submissions
             , SUM(total_accepted_submissions) AS total_accepted_submissions 
        FROM submission_stats 
        GROUP BY challenge_id) ss ON cha.challenge_id = ss.challenge_id
GROUP BY con.contest_id, con.hacker_id, con.name
HAVING SUM(total_submissions)!=0 OR 
       SUM(total_accepted_submissions)!=0 OR
       SUM(total_views)!=0 OR
       SUM(total_unique_views)!=0
ORDER BY contest_id;
```
</details>


<details>
<summary>
<b>55. 15 Days of Learning SQL</b>
</summary>

**Phân tích yêu cầu bài toán:**

Với mỗi ngày _(sorted by the date)_:

- Tính tổng số hacker _(không tính trùng lặp)_ mà đã nộp bài thi mỗi ngày ít nhất một bài.
- Tìm ra tên hacker mà có `hacker_id` thấp nhất trong số những hacker nộp nhiều bài thi nhất. 


```sql
-- Đếm số Submission của mỗi hacker mỗi ngày
WITH SubCount AS
(
SELECT submission_date, hacker_id, COUNT(*) AS Total_sub
FROM Submissions
GROUP BY submission_date, hacker_id
)

-- Từ bảng trên, tìm hacker có max submission và min hacker_id
WITH MaxSubEachDay AS
(
SELECT submission_date
     , hacker_id
     , ROW_NUMBER() OVER (PARTITION BY submission_date 
                          ORDER BY Total_sub DESC, hacker_id) AS Rn
FROM SubCount
)

-- Đánh số hạng cho từng ngày
WITH Rankday AS 
(
SELECT submission_date
     , hacker_id
     , DENSE_RANK() OVER(ORDER BY submission_date) AS DayRn
FROM submissions
)

-- Tạo cột, nếu hôm trước mà xuất hiện hacker thì hôm sau = hôm trước + 1
WITH RankPrevDay AS 
(
SELECT RD.submission_date,
       RD.hacker_id,
       CASE WHEN RD.submission_date = '2016-03-01' THEN 1
            ELSE 1 + (SELECT COUNT(DISTINCT S.submission_date)                         
                      FROM Submissions S 
                      WHERE S.hacker_id = RD.hacker_id 
                        AND S.submission_date < RD.submission_date)
       END AS PrevDayRn,
       RD.DayRn
FROM Rankday RD
)

-- Hacker id cần tìm là những người có PrevDayRn = DayRn
WITH HackerSubEachDay AS 
(
SELECT submission_date
     , COUNT(DISTINCT hacker_id) total_hacker_each_day
FROM RankPrevDay
WHERE PrevDayRn = DayRn
GROUP BY submission_date
)

-- Tổng hợp kết quả
SELECT HS.submission_date
     , HS.total_hacker_each_day
     , M.hacker_id
     , H.name
FROM HackerSubEachDay HS
JOIN MaxSubEachDay M ON HS.submission_date = M.submission_date
JOIN Hackers H ON H.hacker_id = M.hacker_id
WHERE M.Rn = 1
```
</details>

## 8. SQL Advanced Test

<details>
<summary>
<b>1. Weather Analysis</b>
</summary>

```sql
SELECT DATEPART(month, record_date) AS Month
     , max(data_value) AS Max_value
     , min(data_value) AS Min_value
     , FORMAT(AVG(CAST((CASE WHEN data_type = 'avg' THEN data_value END) AS FLOAT)), 'N0') AS Avg_value
FROM temperature_records
GROUP BY DATEPART(month, record_date)
ORDER BY DATEPART(month, record_date)
```
</details>

<details>
<summary>
<b>2. Crypto Market Algorithms Report</b>
</summary>

```sql
SELECT algorithm
     , [1] AS transactions_Q1
     , [2] AS transactions_Q2
     , [3] AS transactions_Q3
     , [4] AS transactions_Q4
FROM
(
SELECT C.algorithm
     , DATEPART(quarter, T.dt) As quarter_2020
     , T.volume
FROM transactions T
JOIN coins C ON T.coin_code = C.code
WHERE DATEPART(year, dt) = 2020
) AS P
PIVOT
(
    SUM(volume) FOR quarter_2020 IN ([1], [2], [3], [4])
) AS PivotTable
```
</details>

<details>
<summary>
<b>3. Winners Chart</b>
</summary>

```sql
WITH first_table AS
(
SELECT event_id
     , participant_name
     , MAX(score) as score
FROM scoretable
GROUP BY event_id, participant_name
),
rank_score AS
(
SELECT event_id
     , participant_name
     , score
     , DENSE_RANK() OVER(PARTITION BY event_id
                                ORDER BY score DESC) AS rank
FROM first_table
),

data_table AS
(
SELECT event_id
     , participant_name
     , MIN(rank) as final_rank
FROM rank_score
WHERE rank in (1, 2, 3)
GROUP BY event_id, participant_name
ORDER BY event_id, final_rank, participant_name OFFSET 0 ROWS
)

SELECT event_id
     , [1] AS first
     , [2] AS second
     , [3] AS third
FROM
(
SELECT event_id, final_rank, STRING_AGG(participant_name, ',') AS concat_name
FROM data_table
GROUP BY event_id, final_rank
) AS PivotData
PIVOT
(
    MAX(concat_name) FOR final_rank in ([1], [2], [3])
) AS PivotTable
```
</details>

<details>
<summary>
<b>4. Weekend Hours Worked</b>
</summary>

```sql
WITH filter_data AS
(
SELECT emp_id
     , timestamp
     , CONVERT(DATE, timestamp) as date
     , CASE WHEN DATEPART(hour, timestamp) <= 12
            THEN 'start_day' ELSE 'end_day' END AS filter
FROM attendance
WHERE DATEPART(weekday, timestamp) in (1, 7)
),
start_date AS
(
SELECT emp_id
     , date
     , timestamp AS start_time
FROM filter_data
WHERE filter = 'start_day'
),
end_date AS
(
SELECT emp_id
     , date
     , timestamp AS end_time
FROM filter_data
WHERE filter = 'end_day'
)

SELECT S.emp_id
     , SUM(DATEDIFF(minute, S.start_time, E.end_time)/60) AS work_hourse
FROM start_date S, end_date E
WHERE S.emp_id = E.emp_id AND S.date = E.date
GROUP BY S.emp_id
ORDER BY work_hourse
```

</details>

## 9. Certificate

Sau khi luyện tập xong, các bạn có thể làm thử bài test để lấy chứng chỉ của [HackerRank](https://www.hackerrank.com/skills-verification). Còn đây là kết quả của mình:

<img class="center-fig" src="./img/hackerrank-basic.png" width=70%>

<img class="center-fig" src="./img/hackerrank-intermediate.png" width=70%>

<img class="center-fig" src="./img/hackerrank-advanced.png" width=70%>

---