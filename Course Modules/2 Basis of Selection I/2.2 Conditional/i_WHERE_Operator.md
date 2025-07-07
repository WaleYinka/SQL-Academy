### 1. Simple filtering on numbers
> [!NOTE]
> Pick good IDs (column good) from Payments table, whose price is greater than 2000. You can find good price in unit_price column.
```sql
SELECT good
FROM Payments
WHERE unit_price > 2000;
```


### 2. Simple filtering on strings
> [!NOTE]
> SELECT family members names (column member_name) from FamilyMembers table, whose status (column status) equals "father"..
```sql
SELECT member_name
FROM FamilyMembers
WHERE STATUS = 'father';
```


### 3. Logical OR
> [!NOTE]
> Output the name (member_name field) and date of birth (birthday field) of family members from the FamilyMembers table whose status (status field) is "father" or "mother".
```sql
SELECT member_name,
	birthday
FROM FamilyMembers
WHERE STATUS = 'father' or status = 'mother';
```


### 4. Logical AND
> [!NOTE]
> You need to get all the rooms, which have both a kitchen (field has_kitchen) and the Internet (field has_internet). Write the request, that satisfies the condition and displays all columns from Rooms table. Availability is indicated by 1 or true, and absence is indicated by 0 or false.
```sql
SELECT *
FROM Rooms
WHERE has_kitchen = 1
	AND has_internet = 1;
```