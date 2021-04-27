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
### use sqlplus run oracle sql ，but rollback if it run error 
```
1. (output to console)
sqlplus $ORACLE_USER/$ORACLE_PASS@$ORACLE_SID 	<<EOF
whenever OSERROR exit 1 rollback;
whenever SQLERROR exit 3 rollback;
@$run_sqlName;
exit;
EOF
2.(output to logfile)
sqlplus $ORACLE_USER/$ORACLE_PASS@$ORACLE_SID >>$sqlfile	<<EOF>> $sqlfile
whenever OSERROR exit 1 rollback;
whenever SQLERROR exit 3 rollback;
@$run_sqlName;
exit;
EOF
```

### sqlplus &&1 ,sqlplus &&2
```
-- run sqlName.sql , let sqlplus &&1 ->spool off 's data save in file1,  sqlplus &&2 ->spool off 's data save in file2

sqlplus dblink sqlName.sql file1  file2

```

