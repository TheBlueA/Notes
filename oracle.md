### get past xxx date of table 
```
select * from test as of timestamp sysdate-400/1440; 
```

copy table structure without data to create a table
```
create table xxx as
select * from test where 1=0
```

