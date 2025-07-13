### Task 21.
> [!NOTE]
> Identify products that have been purchased more than 1 time.
```sql
SELECT good_name
FROM Goods gd
	JOIN Payments pay ON pay.good = gd.good_id
-- WHERE payment_id > 1
GROUP BY good_name
HAVING COUNT(payment_id) > 1;
```

### Task 22.
> [!NOTE]
> Print the names of all mothers.
```sql
SELECT member_name
FROM FamilyMembers
WHERE status = 'mother';
```

### Task 23.
> [!NOTE]
> Find the most expensive delicacy (delicacies) and print its price.
```sql
SELECT good_name,
	unit_price
FROM Goods g
	LEFT JOIN GoodTypes gt ON g.type = gt.good_type_id
	LEFT JOIN Payments py ON g.good_id = py.good
WHERE good_type_name = 'delicacies'
ORDER BY unit_price DESC
LIMIT 1;
```

### Task 24.
> [!NOTE]
> Determine who spent how much in June 2005.
```sql
SELECT member_name,
	SUM(amount * unit_price) AS costs
FROM FamilyMembers
	JOIN Payments ON member_id = family_member
WHERE MONTH(date) = 6
	AND YEAR(date) = 2005
GROUP BY member_name;
```

### Task 25.
> [!NOTE]
> Determine which products were not purchased in 2005.
```sql
SELECT good_name
FROM Goods
WHERE good_id NOT IN (
		SELECT good
		FROM Payments
		WHERE YEAR(date) = 2005
	);
```

### Task 26.
> [!NOTE]
> Identify groups of products that were not purchased in 2005.
```sql
SELECT good_type_name
FROM GoodTypes
WHERE good_type_id NOT IN (
		SELECT type
		FROM Goods
		JOIN Payments ON good = good_id
		WHERE YEAR(date) = 2005
	);
```

### Task 27.
> [!NOTE]
> Identify products that have been purchased more than 1 time.
```sql
SELECT good_type_name,
	SUM(amount * unit_price) AS costs
FROM GoodTypes
	JOIN Goods ON good_type_id = TYPE
	JOIN Payments ON good_id = good
WHERE YEAR(date) = 2005
GROUP BY good_type_name;
```

### Task 28.
> [!NOTE]
> How many trips were made by airlines from Rostov to Moscow?
```sql
SELECT COUNT(id) AS COUNT
FROM Trip
WHERE town_from = 'Rostov'
	AND town_to = 'Moscow';
```

### Task 29.
> [!NOTE]
> Print the names of passengers who flew to Moscow on TU-134. There should be no duplicates in the response.
```sql
SELECT DISTINCT name
FROM Passenger ps
	LEFT JOIN Pass_in_trip pt ON pt.passenger = ps.id
	LEFT JOIN Trip t ON t.id = pt.trip
WHERE town_to = 'Moscow'
	AND plane = 'TU-134';
```

### Task 30.
> [!NOTE]
> Output the load (number of passengers) of each trip . Output the result in sorted form in descending order of load.
```sql
SELECT trip, COUNT(passenger) AS count
FROM Pass_in_trip pt
	LEFT JOIN Trip t ON t.id = pt.trip
GROUP BY trip
ORDER BY count DESC;
```

### Task 31.
> [!NOTE]
> Print all family members with the last name Quincey.
```sql
SELECT *
FROM FamilyMembers
WHERE SUBSTRING_INDEX(member_name, ' ', -1) = 'Quincey';
```

### Task 32.
> [!NOTE]
> Display the average age of people (in years) stored in the database. The result is rounded down to the nearest integer.
```sql
SELECT FLOOR(AVG(TIMESTAMPDIFF(YEAR, birthday, CURDATE()))) AS age
FROM FamilyMembers;
```

### Task 33.
> [!NOTE]
> Find the average price of caviar based on the data stored in the Payments table. The database stores data on purchases of red caviar and black caviar. The query result should contain one line with the average price of all caviar ever bought.
```sql
SELECT AVG(unit_price) AS cost
FROM Payments
	JOIN Goods ON good_id = good
WHERE good_name LIKE '%caviar%';
```

### Task 34.
> [!NOTE]
> How many 10th grades are there in total
```sql
SELECT COUNT(*) AS count
FROM Class
WHERE name LIKE '%10%';
```

### Task 35.
> [!NOTE]
> How many different classrooms of the school were used on September 2, 2019 for classes?
```sql
SELECT COUNT(DISTINCT classroom) AS count
FROM Schedule
WHERE DATE_FORMAT(date, '%e.%m.%Y') = '2.09.2019';;
```

### Task 36.
> [!NOTE]
> Print information about students living on Pushkin street (ul. Pushkina)?
```sql
SELECT *
FROM Student
WHERE address LIKE '%ul. Pushkina%';
```

### Task 37.
> [!NOTE]
> How old is the youngest student ?
```sql
SELECT MIN(TIMESTAMPDIFF(YEAR, birthday, CURDATE())) AS year
FROM Student;;
```

### Task 38.
> [!NOTE]
> How many Ann (Anna) goes to school?
```sql
SELECT COUNT(*) as count
FROM Student
WHERE first_name LIKE 'Ann%';
```

### Task 39.
> [!NOTE]
> How many students are in grade 10 B ?
```sql
SELECT COUNT(sc.student) AS COUNT
FROM Student_in_class sc
	JOIN Class c ON c.id = sc.class
WHERE c.name = '10 B';
```

### Task 40.
> [!NOTE]
> Print the names of the subjects taught by Romashkin P.P. Note that there are multiple teachers with the same last name in the database.
```sql
SELECT sb.name AS subjects
FROM Subject sb
	LEFT JOIN Schedule sc ON sb.id = sc.subject
	LEFT JOIN Teacher t ON t.id = sc.teacher
WHERE t.first_name LIKE 'P%'
	AND t.middle_name LIKE 'P%'
	AND t.last_name = 'Romashkin';
```