### 1. Print unique names
> [!NOTE]
> Print only the unique values of first_name from the table Student.
```sql
SELECT DISTINCT first_name
FROM Student;
```

### 2. Print unique column pairs
> [!NOTE]
> Print only unique value pairs of teacher ID teacher and subject ID subject from Schedule.
```sql
SELECT DISTINCT teacher,
	subject
FROM Schedule;
```