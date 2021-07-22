### Oracle(19c) ORA-01417: a table may be outer joined to at most one other table  

Error sql: 
```
SELECT *
 FROM 
 (
    SELECT a.acct, b.con
    FROM a, b
    WHERE a.acct = b.acct AND b.con = ''
 ) acc 
 LEFT  JOIN 
 (
   SELECT ACCT, CON, max(abc) max FROM c GROUP BY ACCT, CON
 ) b
 ON b.ACC = acc.ACCT AND b.CON = acc.CON
 LEFT  JOIN  c
 ON b.acct = c.acct and b.con = c.con and b.max = c.abc  

```
Cause:
acc's value acct and con are come from different table , and they are also join b and c 's condition, 

Solution :




