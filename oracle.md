### get past xxx date of table 
```
select * from test as of timestamp sysdate-400/1440; 
```

### copy table structure without data to create a table
```
create table xxx as
select * from test where 1=0
```

### search  jobs of database 
```
select * from user_jobs
where what like '%*%'
```

### search proc content of databse 
```  
select * from user_source
where Text like '%JOB_DAILY_REFRESH_SALES_MV%'

```
