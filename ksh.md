### ksh(KornShell)


命令行模式下按下 Esc 键后，可通过

 + ESC+k 上一条命令

 + ESC+j 下一条命令

 + ESC++ 上一条命令

 + ESC+- 下一条命令

 + ESC+\ 自动补全文件名

 + ESC+h 在命令行中往前移动光标

 + ESC+l 在命令行中往后移动光标

 + 退格键：可用 Ctrl + H 来实现。

 + 删除整行：Ctrl + U

 + 删除光标之前的一个单词：Ctrl + W


原文链接：https://blog.csdn.net/zzk00007/article/details/96868057

----

### Send email
After input the main content of email , Press Ctrl + D and  would display EOT
```
mailx/mail -s  "subject Name" emailAddress
hi, 
xxx
(main content)
EOT
```

## use shell to send eamil 
content  can be use **\n**   to implement line feed

1. 
```
print $content | mailx -s "$subject" -c $cc_email_list "$email_list" 
eg：
print "${sql_log}\n testmailx" | mailx -s "text test "  "xxx@outlook.com"  

```
2.
```
send_email_withCC xx.txt "subject " \
"Hi all,
xxx : ${text}" \
"xxx@xx.com"  "xxx@xx.com" 

send_email_withCC()
{
  typeset logfile=$1
  typeset subject=$2
  typeset content=$3
  typeset email_list=$4
  typeset cc_email_list=$5
  [ "$logfile" = "" ] || typeset logfilename=`basename $logfile`
  
  mailx -s "$subject" -c $cc_email_list "$email_list" <<EOF
$content
EOF

# print $content | mailx -s "$subject" -c $cc_email_list "$email_list" 

}

```

3.  send email with attachment
 ```
 (print $content; uuencode $logfile $logfilename ) | mailx   -s "$subject" -c $cc_email_list "$email_list" 
```

-----

+ $0	当前脚本的文件名
+ $n	传递给脚本或函数的参数。n 是一个数字，表示第几个参数。例如，第一个参数是$1，第二个参数是$2。
+ $#	传递给脚本或函数的参数个数。
+ $*	传递给脚本或函数的所有参数。
+ $@	传递给脚本或函数的所有参数。被双引号(" ")包含时，与 $* 稍有不同，下面将会讲到。
+ $?	上个命令的退出状态，或函数的返回值。
+ $$	当前Shell进程ID。对于 Shell 脚本，就是这些脚本所在的进程ID。

----
tee 从标准输入设备读取数据，将其内容输出到标准输出设备
- -a或--append 　附加到既有文件的后面，而非覆盖它．
- -i或--ignore-interrupts 　忽略中断信号。
- --help 　在线帮助。
- -version 　显示版本信息。

ls -ltr s*  show deatails of start with s 
