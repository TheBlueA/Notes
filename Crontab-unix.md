### Crontab

#### Cron Table Format

```
*    *    *   *    *  Command_to_execute
|    |    |    |   |       
|    |    |    |    Day of the Week ( 0 - 6 ) ( Sunday = 0 )
|    |    |    |
|    |    |    Month ( 1 - 12 )
|    |    |
|    |    Day of Month ( 1 - 31 )
|    |
|    Hour ( 0 - 23 )
|
Min ( 0 - 59 )
````

##### Specifying multiple values in a field
The asterisk (*) operator specifies all possible values for a field. e.g. every hour or every day.

The comma (,) operator specifies a list of values, for example: "1,3,4,7,8".

The dash (-) operator specifies a range of values, for example: "1-6", which is equivalent to "1,2,3,4,5,6".

The slash (/) operator, can be used to skip a given number of values. For example, "*/3" in the hour time field is equivalent to "0,3,6,9,12,15,18,21"; "*" specifies 'every hour' but the "/3" means that only the first, fourth, seventh...and such values given by "*" are used.

Cron will email to the user all output of the commands it runs, to silence this, redirect the output to a log file or to /dev/null.


##### Examples：
    
   1. To run /usr/bin/sample.sh at 12.59 every day and supress the output   
      ```    59 12 * * * simon /usr/bin/sample.sh> / dev / null 2>＆1    ```

----

#### Crontab Options

1. Install or update job in crontab, use -e option:
``` $crontab -e ```

2. To List Crontab entries, use -l option:
``` $ crontab -l```

3. To Deinstall job from crontab, use -r option:
``` $ crontab -r ```

4. To Confirm Deinstall of job from crontab, use -i option:
``` $ crontab -i -r ```

5. To add SELINUX security to crontab file, use -s option:
``` $ crontab -s ```

6. To edit other user crontab, user -u option and specify username:
``` $ crontab -u username -e ```

7. To List other user crontab entries:
``` $ crontab -u username -l ```

crontab online calculation tool : https://tool.lu/crontab/

