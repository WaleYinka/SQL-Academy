### 1. Print string in lowercase
> [!TASK]
> Print the text "Hello world" in lowercase using the corresponding function. To print text, use the alias lower_string.
```sql
SELECT LOWER('Hello world') AS lower_string;
```

### 2. Print year of date
> [!TASK]
> Print the full name of the family member and his year of birth using the YEAR function. Use the alias year_of_birth to display the year of birth.
```sql
SELECT member_name, YEAR(birthday) AS year_of_birth
FROM FamilyMembers;
```

### 3. Last name length calculation
> [!TASK]
> Print the full name of the family member and the length of their last name. Use the lastname_length alias to display the length of the last name.
```sql
SELECT member_name,
	LENGTH(member_name) - INSTR(member_name, ' ') AS lastname_length
FROM FamilyMembers;
```