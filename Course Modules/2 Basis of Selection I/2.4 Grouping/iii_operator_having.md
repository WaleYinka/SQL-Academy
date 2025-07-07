### 1. Group filtering
> [!NOTE]
> Print the types of rooms (the field home_type) and the difference between the most expensive and the cheapest representative of this type. Include in the final sample only those types of housing, whose number in the Rooms table is greater than or equal to 2.
To display cost differences, use the difference alias.
```sql
SELECT home_type,
	(Max(price) - min(price)) AS difference
FROM Rooms
GROUP BY home_type
HAVING COUNT(*) >= 2;
```