### 1. Grouping and sorting
> [!NOTE]
> Count the number of students in each class and also sort them in descending order of the number of students. You can get the student's belonging to a specific class from the Student_in_class. table. As a result, display the class identifier (class field) and the number of students in this class. 
Use the count alias to display the number of students.
```sql
SELECT class, count(id) AS count
FROM Student_in_class
GROUP BY class 
ORDER BY count DESC;
```


### 2. Aggregation functions MIN and MAX
> [!NOTE]
> For each existing status, find the oldest person (use birthday field). Display the status and date of birth.
Use the birthday alias to display the date of birth.
```sql
SELECT STATUS,
	min(birthday) AS birthday
FROM FamilyMembers
GROUP BY STATUS;
```


### 3. Aggregation function AVG
> [!NOTE]
> Get the average flight time for each aircraft model. Output the plane field and the average flight time in seconds.
Use the time alias to display the time.
Use TIMESTAMPDIFF(second, time_out, time_in) function to get the time difference in seconds between two dates.
```sql
SELECT plane,
	avg(timestampdiff(SECOND, time_out, time_in)) AS time
FROM trip
GROUP BY plane;
```


### 4. SELECTing using multiple aggregation functions
> [!NOTE]
> Output the room ID (field room_id), the average cost for one day of rent (the price field, use the avg_price alias for display), and the number of reservations for this room (use the count alias). Sort the result in descending order, first by the number of reservations, and then by the average cost.
```sql
SELECT room_id,
	avg(price) AS avg_price,
	COUNT(id) AS count
FROM Reservations
GROUP BY room_id
ORDER BY COUNT DESC,
	avg_price DESC;
```