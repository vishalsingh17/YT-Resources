#### 1. Insert data in selected columns 
```sql
insert into employee(emp_id, emp_name) value (7, "Niharika");
```

#### 2. Create sub table/ replica table from existing table
```sql
create table sub_emp as select emp_id, emp_name from employee;
```

#### 3. Fetch data from table
```sql
select * from sub_emp;
```

### 4. Delete table
```sql
drop table sub_emp;
```

For detailed explanation: [YouTube Video](https://www.youtube.com/watch?v=cEZ56906cWk&list=PL53IeEJJLQl3xIzMPqA7lApebsB-UqtNB&index=8)
