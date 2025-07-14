### Task 41.
> [!NOTE]
> Find out what time the fourth lesson starts according to the schedule.
```sql
SELECT DISTINCT tp.start_pair
FROM Timepair tp
	JOIN Schedule sc ON tp.id = sc.number_pair
WHERE tp.id = 4;
```

### Task 42.
> [!NOTE]
> How long will the student be in school, studying from the 2nd to the 4th academic subject?
```sql
SELECT TIMEDIFF(MAX(end_pair), MIN(start_pair)) AS time
FROM Timepair
WHERE id BETWEEN 2 AND 4;
```

### Task 43.
> [!NOTE]
> Print the last names of the teachers who teach physical education (Physical Culture). Sort the teachers by last name in alphabetical order.
```sql
SELECT last_name
FROM Teacher
	LEFT JOIN Schedule ON Teacher.id = Schedule.teacher
	LEFT JOIN Subject ON Schedule.subject = Subject.id
WHERE Subject.name = 'Physical Culture'
ORDER BY last_name;
```

### Task 44.
> [!NOTE]
> Find the maximum age among the students in the 10th classes today. To retrieve the current date and time, you can use the NOW() function.
```sql
SELECT MAX(TIMESTAMPDIFF(YEAR, birthday, NOW())) AS max_year
FROM Student st
	JOIN Student_in_class sic ON st.id = sic.student
	JOIN Class c ON sic.class = c.id
WHERE c.name LIKE '%10%';
```

### Task 45.
> [!NOTE]
> Which classrooms were most often used for classes? Output the ones that have been used the maximum number of times.
```sql
SELECT classroom
FROM Schedule
GROUP BY classroom
HAVING count(classroom) = (
    SELECT COUNT(*) AS count
    FROM Schedule
    GROUP BY classroom
    ORDER BY count DESC
    LIMIT 1
);
```

### Task 46.
> [!NOTE]
> In which classes will the Krauze teacher introduce classes ?
```sql
SELECT  c.name
FROM Class c
	JOIN Schedule s ON c.id = s.class
	JOIN Teacher t ON t.id = s.teacher
WHERE t.last_name = 'Krauze'
GROUP BY c.name;
```

### Task 47.
> [!NOTE]
> How many classes did Krauze hold on August 30, 2019?
```sql
SELECT  COUNT(*) AS count
FROM Schedule s
	JOIN Teacher t ON t.id = s.teacher
-- WHERE t.last_name = 'Krauze' AND YEAR(date) = 2019 AND MONTH(date) = 08 AND DAY(date) = 30;
WHERE DATE_FORMAT(date, '%e %M %Y') = '30 August 2019'
  AND t.last_name = 'Krauze';;
```

### Task 48.
> [!NOTE]
> Print the number of students in classes in descending order
```sql
SELECT name,
	COUNT(student) AS count
FROM Class c
	JOIN Student_in_class sic ON c.id = sic.class
GROUP BY name
ORDER BY count DESC;
```

### Task 49.
> [!NOTE]
> What percentage of students study in the "10 A" class? Print the answer in the range from 0 to 100 rounded to four decimal places, e.g, 96.0201.
```sql
SELECT COUNT(*) * 100 / (
    SELECT COUNT(*)
    FROM Student_in_class
) AS percent
FROM Student_in_class sc
         JOIN Class cs ON cs.id = sc.class
WHERE name = '10 A';
```

### Task 50.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 51.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 52.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 53.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 54.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 55.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 56.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 57.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 58.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 59.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```

### Task 60.
> [!NOTE]
> What percentage of students were born in 2000? The result of rounding to the nearest whole in the smaller side.
```sql
SELECT FLOOR(
		COUNT(*) * 100.0 /
		(SELECT COUNT(*)
		FROM Student)
	) AS percent
FROM Student
WHERE YEAR(birthday) = 2000;
```