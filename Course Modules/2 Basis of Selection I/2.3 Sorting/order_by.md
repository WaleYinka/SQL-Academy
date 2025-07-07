### 1. Descending sort
> [!NOTE]
> For each individual payment, print the good identificator and the sum of the money spent on it, sorted in descending order of this sum of the money. The list of payments is in the Payments table. To display the sum of the money use sum alias.
```sql
SELECT good,
	SUM(amount * unit_price) AS sum
FROM Payments
GROUP BY good
ORDER BY sum DESC;
```


### 2. Multi column sort
> [!NOTE]
> Output all the data of family members with the surname Quincey from the FamilyMembers table and sort them in ascending order first by the status column, and then by member_name.
```sql
SELECT *
FROM FamilyMembers
WHERE member_name LIKE "%Quincey%"
ORDER BY STATUS ASC,
	member_name;
```