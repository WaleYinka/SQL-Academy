### Task 1.
> [!NOTE]
> Print the names of all the people who are in the airline database.
```sql
SELECT name
FROM Passenger;
```

### Task 2.
> [!NOTE]
> Print the names of all airlines.
```sql
SELECT name
FROM Company;
```

### Task 3.
> [!NOTE]
> Print all trips made from Moscow.
```sql
SELECT *
FROM Trip
WHERE town_from = "Moscow";
```

### Task 4.
> [!NOTE]
> Print the names of people that end in "man".
```sql
SELECT name
FROM Passenger
WHERE name LIKE "%man";
```

### Task 5.
> [!NOTE]
> Print the number of trips completed on TU-134.
```sql
SELECT COUNT(*) AS count
FROM Trip
WHERE plane = "TU-154";
```

### Task 6.
> [!NOTE]
> Which companies have flown on Boeing.
```sql
SELECT DISTINCT name
FROM Company
	JOIN Trip ON Company.id = Trip.company
WHERE plane = "Boeing";
```

### Task 7.
> [!NOTE]
> Display all the names of aircraft that you can fly to Moscow.
```sql
SELECT DISTINCT plane
FROM Trip
WHERE town_to = 'Moscow';
```

### Task 8.
> [!NOTE]
> What cities can I fly to from Paris and how long will it take?
```sql
SELECT town_to, (TIMEDIFF(time_in, time_out)) AS flight_time
FROM Trip
WHERE town_from = 'Paris';
```

### Task 9.
> [!NOTE]
> What companies organize flights from Vladivostok?
```sql
SELECT Company.name
FROM Company
JOIN Trip
ON Company.id = Trip.company
WHERE town_from = 'Vladivostok';
```

### Task 10.
> [!NOTE]
> Print trips made from 10 a.m. to 2 p.m. on January 1, 1900.
```sql
SELECT *
FROM Trip
WHERE time_out >= '1900-01-01T10:00:00.000Z'
  AND time_out <= '1900-01-01T14:00:00.000Z';
/* WHERE DATE(time_out) = '1900-01-01'
  AND TIME_FORMAT(time_out, '%H:%i') >= '10:00'
  AND TIME_FORMAT(time_out, '%H:%i') <= '14:00'; */
```

### Task 11.
> [!NOTE]
> Print the passengers with the longest full name. Spaces, hyphens, and dots are considered part of the name.
```sql
SELECT name
FROM passenger
WHERE LENGTH(name) = (
    SELECT MAX(LENGTH(name))
    FROM passenger); 
``` 

### Task 12.
> [!NOTE]
> Print the IDs of all flights and the number of passengers on each flight. If there are no passengers on a flight, print the number "0" for that flight.
```sql
SELECT t.id,
	COALESCE(COUNT(p.passenger)) AS count
FROM Trip AS t
	LEFT JOIN Pass_in_trip AS p 
	ON t.id = p.trip
GROUP BY t.id;
```

### Task 13.
> [!NOTE]
> Display the names of people who have a full namesake among passengers.
```sql
SELECT DISTINCT name
FROM Passenger
GROUP BY name
HAVING COUNT(*) > 1; 
```

### Task 14.
> [!NOTE]
> Which cities did Bruce Willis visit.
```sql
SELECT town_to
FROM Trip AS t
	LEFT JOIN Pass_in_trip AS pt ON t.id = pt.trip
	LEFT JOIN Passenger AS ps ON pt.passenger = ps.id
WHERE ps.name = 'Bruce Willis';
```

### Task 15.
> [!NOTE]
> Print the passenger ID of Steve Martin and the date and time of his arrival in London.
```sql
SELECT ps.id, t.time_in
FROM Trip AS t
	LEFT JOIN Pass_in_trip AS pt ON t.id = pt.trip
	LEFT JOIN Passenger AS ps ON pt.passenger = ps.id
WHERE ps.name = 'Steve Martin'
AND town_to = 'London'; 
```

### Task 16.
> [!NOTE]
> Display the list of passengers sorted by the number of flights (in descending order) and name (in ascending order) who have made at least 1 flight. 
```sql
SELECT name,
	COUNT(name) AS COUNT
FROM Passenger AS ps
	JOIN Pass_in_trip AS pt ON ps.id = pt.passenger
	JOIN Trip AS tr ON pt.trip = tr.id
GROUP BY name
ORDER BY COUNT DESC,
	name ASC;
```

### Task 17.
> [!NOTE]
> Determine how much each family member spent in 2005. In the resulting sample, do not output those family members who have not spent anything. 
```sql
SELECT member_name,
    status,
	SUM(unit_price * amount) AS costs
FROM FamilyMembers AS fm
	INNER JOIN Payments AS p 
	ON fm.member_id = p.family_member
WHERE p.date LIKE "%2005%"
--WHERE YEAR(p.date) = 2005
GROUP BY member_name, +status;
```

### Task 18.
> [!NOTE]
> Print the name of the oldest person. If there are several of them, then output them all.
```sql
SELECT member_name
FROM FamilyMembers
WHERE birthday = (
		SELECT MIN(birthday)
		FROM FamilyMembers
	);
```

### Task 19.
> [!NOTE]
> Determine which family member bought potatoes (potato).
```sql
SELECT status
FROM FamilyMembers fm
	LEFT JOIN Payments p ON p.family_member = fm.member_id
	LEFT JOIN Goods g ON g.good_id = p.good
WHERE good_name LIKE '%potato%'
GROUP BY status;
```

### Task 20.
> [!NOTE]
> How much and who from the family spent on entertainment. Print family status, name, amount.
```sql
SELECT status,
	member_name,
	SUM(unit_price * amount) AS costs
FROM FamilyMembers fm
	LEFT JOIN Payments p ON p.family_member = fm.member_id
	LEFT JOIN Goods g ON g.good_id = p.good
	LEFT JOIN GoodTypes gt ON gt.good_type_id = g.type
WHERE good_type_name = 'entertainment'
GROUP BY member_name,
	status;
```