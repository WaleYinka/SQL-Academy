### 1. Print string
> [!TASK]
> Using SELECT operator to print the text "Hello world".
```sql
SELECT "Hello world";
```

### 2. SELECTing all columns
> [!TASK]
> Select all columns from Payments table.
```sql
SELECT * FROM Payments;
```

### 3. SELECTing by multiple columns
> [!TASK]
> Pick member_id, member_name and status fields from FamilyMembers table.
```sql
SELECT member_id,
	member_name,
	status
FROM FamilyMembers
```

### 4. Print with alises
> [!TASK]
> Print the name field from the Passenger table. When displaying this field, use the alias "passengerName"
```sql
SELECT name AS passengerName
FROM Passenger;
```