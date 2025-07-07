### 1. Restricting entries from the beginning of the table
> [!NOTE]
> Sort the list of companies (Company table) by the name in ascending order and display first two records.
```sql
SELECT *
FROM company
ORDER BY name ASC
LIMIT 2;
```


### 2. Limit the number of offset entries
> [!NOTE]
> Print the beginning (start_pair field) and the end (end_pair field) of the second and third lessons from the table Timepair.
```sql
SELECT start_pair,
	end_pair
FROM Timepair
LIMIT 1, 2
```