### Task 6.
> [!NOTE]
> Which companies have flown on Boeing. Fields in the resulting table:name
```sql
SELECT DISTINCT name
FROM Company
	JOIN Trip ON Company.id = Trip.company
WHERE plane = "Boeing"
```


### Task 7.
> [!NOTE]
> Display all the names of aircraft that you can fly to Moscow. Fields in the resulting table:plane
```sql
SELECT DISTINCT plane
FROM Trip
WHERE town_to = 'Moscow' 
```


### Task 8.
> [!NOTE]
> What cities can I fly to from Paris and how long will it take? Fields in the resulting table:town_to, flight_time. Use the "as flight_time" construct to output the required time. This is necessary for correct verification.The format for the output time: HH:MM:SS
```sql
SELECT town_to, (TIMEDIFF(time_in, time_out)) AS flight_time
FROM Trip
WHERE town_from = 'Paris' 
```


### Task 9.
> [!NOTE]
> What companies organize flights from Vladivostok? Fields in the resulting table:name
```sql
SELECT Company.name
FROM Company
JOIN Trip
ON Company.id = Trip.company
WHERE town_from = 'Vladivostok' 
```


### Task 10.
> [!NOTE]
> Print trips made from 10 a.m. to 2 p.m. on January 1, 1900. Fields in the resulting table:*
```sql
SELECT *
FROM Trip
WHERE time_out >= '1900-01-01T10:00:00.000Z'
  AND time_out <= '1900-01-01T14:00:00.000Z'; 
```