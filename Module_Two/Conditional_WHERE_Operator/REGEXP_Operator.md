### 1. Search by substring
> [!NOTE]
> Find all Rooms whose address contains the string ‘Avenue’. In the resulting selection, display the fields id and address.
```sql
SELECT id,
	address
FROM Rooms
WHERE address LIKE '%Avenue%';
```

### 2. Search by email address
> [!NOTE]
> Display the name and email of users whose email address ends with "@outlook.com" or "@live.com".
```sql
SELECT name,
	email
FROM Users
WHERE email REGEXP '@(outlook.com|live.com)$';
```