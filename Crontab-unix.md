### Crontab (Unix)

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

Reprinted from https://www.tutorialspoint.com/unix_commands/crontab.htm

-----

### crontab 常见 /dev/null 2>&1 详解

大部分 crontab 计划任务，在命令行末尾都会带 >/dev/null 2>&1，它的作用是什么呢？

``` 59 12 * * * simon /usr/bin/sample.sh> /dev/null 2>＆1 ``` 

以下为其详解：

+  `>` 代表重定向；

+ /dev/null 代表空设备文件，相当于回收站。null是一个名叫null小桶的东西，将输出重定向到它的好处是:不会因为输出的内容过多而导致文件大小不断的增加，也就是将命令的输出扔掉了。

+ **1 表示stdout标准输出**，系统默认值是1，所以">/dev/null" 等同于 "1>/dev/null"

+ **2 表示stderr标准错误输出**；

+ & 表示等同于的意思，2>&1表示将标准错误输出重定向到标准输出stdout。

**整句的意思就是标准输出重定向到空设备文件，也就是不输出任何信息到终端，标准错误输出重定向等同于标准输出，因为之前标准输出已经重定向到了空设备文件，所以标准错误输出也重定向到空设备文件。**

#### command > file 2>file 与 command > file2>&1 区别

1. command >file 2>file含义

- 表示将命令所产生的标准输出信息，和错误的输出信息送到file 中。但是file会被打开两次，而且stdout和stderr会互相覆盖，这样写相当于使用了FD1和FD2两个同时去抢占file 的管道。

2. command >file 2>&1 含义

- 表示将stdout直接送向file， stderr 继承了FD1管道后，再被送往file，此时，file 只被打开一次，也只使用了一个管道FD1，它包括了stdout和stderr的全部内容。从IO效率上讲，前一条命令的效率比后一条命令的效率要低，所以在编写shell脚本时，我们较多会用**command > file 2>&1** 这样的写法。


