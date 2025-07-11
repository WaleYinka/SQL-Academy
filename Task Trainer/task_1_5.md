### Task 1.
> [!NOTE]
> Print the names of all the people who are in the airline database.
Fields in the resulting table:name.
```sql
SELECT name
FROM Passenger;
```


### Task 2.
> [!NOTE]
> Print the names of all airlines.
Fields in the resulting table:name
```sql
SELECT name
FROM Company;
```


### Task 3.
> [!NOTE]
> Print all trips made from Moscow.
Fields in the resulting table:*
```sql
SELECT *
FROM Trip
WHERE town_from = "Moscow";
```


### Task 4.
> [!NOTE]
> Print the names of people that end in "man".
Fields in the resulting table:name
```sql
SELECT name
FROM Passenger
WHERE name LIKE "%man";
```


### Task 5.
> [!NOTE]
> Print the number of trips completed on TU-134.
Fields in the resulting table:count. Use the "as count" construct for the aggregate function of counting the number of trips. This is necessary for validation.
```sql
SELECT COUNT(*) AS count
FROM Trip
WHERE plane = "TU-154"
```