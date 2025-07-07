### 1. Number of rooms by type
> [!NOTE]
> Group the data from the Rooms table by the home_type field and display the housing type and the number of rooms of each type. Use the alias count_rooms for the number of rooms.
```sql
SELECT home_type,
	COUNT(id) AS count_rooms
FROM Rooms
GROUP BY home_type;
```

### 2. Average price by type and TV
> [!NOTE]
> Group the data from the Rooms table by the home_type and has_tv fields. Display the housing type, TV availability (0 or 1), and the average price for each group. Use the alias avg_price for the average price.
```sql
SELECT home_type,
	has_tv,
	avg(price) AS avg_price
FROM Rooms
GROUP BY home_type,
	has_tv;
```