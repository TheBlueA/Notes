## use docker to install php running environment

1. docker pull php:7.3.15-fpm
 
   1.1 run php
   
   ``` docker run --name myphp -p 9000:9000 -v d:/php/www:/var/www -d php:7.3.15 ```
2. docker pull nginx:1.15.12
    2.1 run nginx (**/var/www need mapping to project code repository**)
     
     ``` docker run --name mynginx -p 80:80 -v d:/php/www:/var/www  -d nginx:1.15.12 ```
  
    2.2 use **docker exec -it PID /bin/bash** into the container, modify **default.conf**  （/etc/nginx/conf.d/default.conf), different versions of nginx, conf files may not be here
, can use **find . -name *default.conf** to search 
```
   default.conf
   
   server {
    listen       80;
    server_name  localhost;
    root 		 /var/www;
    index		 index.php;

  
	# deny accessing php files for the /assets directory
    location ~ ^/assets/.*\.php$ {
        deny all;
    }

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
        try_files $uri =404;
    }

	location ~* /\. {
        deny all;
    }

}

docker inspect --format='{{.NetworkSettings.IPAddress}}' +contrainer_name  can get ipaddress of running contrainer  
eg:
docker inspect --format='{{.NetworkSettings.IPAddress}}' myphp
```

# connection mysql failed

error message :

SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client

run sql in mysql : 
```
use mysql;
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
```
