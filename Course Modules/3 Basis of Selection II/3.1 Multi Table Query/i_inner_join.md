### 1. INNER JOIN
> [!NOTE]
> Join the Class and Student_in_class tables using an inner join on the Class.id and Student_in_class.class fields. Print the class name (Class.name field) and student ID (Student_in_class.student field).
```sql
SELECT Class.name,
	Student_in_class.student
FROM Class
	INNER JOIN Student_in_class ON class.id = Student_in_class.class;
```


### 2. Multi table INNER JOIN
> [!NOTE]
> Append the query from the previous assignment by adding another inner join to the Student table. Combine the Student_in_class.student and Student.id fields and print the student's name (first_name field) instead of the student ID.
```sql
SELECT Class.name,
	first_name
FROM Class
	INNER JOIN Student_in_class ON class.id = Student_in_class.class
	INNER JOIN Student ON Student_in_class.student = Student.id;
```


### 3. Multi table INNER JOIN with filtration
> [!NOTE]
> Print the names of products that a family member with the "son" status bought. To get a selection, you need to join the Payments table with the FamilyMembers table for the family_member and member_id fields, and the Goods table for the good and good_id fields.
```sql
SELECT good_name
FROM Payments
	JOIN FamilyMembers ON Payments.family_member = FamilyMembers.member_id
	JOIN Goods ON Payments.good = Goods.good_id
WHERE FamilyMembers.status = "son";
```


### 4. INNER JOIN with grouping
> [!NOTE]
> Print the identifier (the room_id field) and the average rating of the room (the rating field, for display use the avg_score alias), based on reviews from the Reviews table.
This table is linked to Reservations (the table where you can get the room ID) by the reservation_id and Reservations.id fields.
```sql
SELECT room_id,
	avg(rating) AS avg_score
FROM Reservations
	JOIN Reviews ON Reservations.id = Reviews.reservation_id
GROUP BY Reservations.room_id;
```