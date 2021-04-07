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
### sqlplus if error rollback
```
1. (output console)
sqlplus $ORACLE_USER/$ORACLE_PASS@$ORACLE_SID 	<<EOF
whenever OSERROR exit 1 rollback;
whenever SQLERROR exit 3 rollback;
@$run_sqlName;
exit;
EOF
2.(output logfile)
sqlplus $ORACLE_USER/$ORACLE_PASS@$ORACLE_SID >>$sqlfile	<<EOF>> $sqlfile
whenever OSERROR exit 1 rollback;
whenever SQLERROR exit 3 rollback;
@$run_sqlName;
exit;
EOF
```


