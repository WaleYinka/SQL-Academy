### 1. Filtering by string pattern
> [! TASK]
> Find all family members with the lastname "Quincey" and output the field member_name.
```sql
SELECT member_name 
FROM FamilyMembers
WHERE member_name LIKE "%Quincey%";
```