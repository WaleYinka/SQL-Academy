### 1. Print records containing NULL
> [! TASK]
> Print the first_name and last_name of the students from the table Student missing middle_name.
```sql
SELECT first_name,
	last_name
FROM Student
WHERE middle_name IS NULL;
```

### 2. Looking for values in a specified range
> [! TASK]
> Select room reservations (columns room_id, start_date, end_date) from Reservations table, whose total price (column total) is between 500 and 1200.
```sql
SELECT room_id,
	start_date,
	end_date
FROM Reservations
WHERE total BETWEEN 500 AND 1200;
```

### 3. Looking for values in a specific list
> [! TASK]
> Output information about students from the table Student, whose year of birth corresponds to one of the following: 2000, 2002 and 2004.
```sql
SELECT *
FROM Student
WHERE YEAR(birthday) IN (2000, 2002, 2004);
```