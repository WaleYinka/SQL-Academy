### 1. Left outer join
> [!NOTE]
> Print the name first_name and the last name last_name of each teacher from the table Teacher, as well as the number of classes in which he was appointed a teacher. If the teacher has not been assigned to any class, then output 0.
Use the alias amount_classes to display the number of classes.
```sql
SELECT Teacher.first_name,
	Teacher.last_name,
	COUNT(Schedule.id) AS amount_classes
FROM Teacher
	LEFT JOIN Schedule ON Teacher.id = Schedule.teacher
GROUP BY Teacher.id;
```