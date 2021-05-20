## craftCMS can not running and show GD and zip error 

## install gd extension

1.  install dependency extension of gd
 
 ``` apt-get update && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev libpng-dev```

2.  extract source code
```docker-php-source extract ```

3. compile & install

```
cd /usr/src/php/ext/gd

docker-php-ext-configure gd --with-webp-dir=/usr/include/webp --with-jpeg-dir=/usr/include --with-png-dir=/usr/include --with-freetype-dir=/usr/include/freetype2

docker-php-ext-install gd
```

4. check 

```
php -m | grep gd
```

5. restart php container

##  install zip extension in php(docker) 

1. install dependency extension of zip  
   
   ```apt-get update && apt-get install -y zlib1g-dev && apt-get install -y libzip-dev```

2. install & start zip extension 

   ```docker-php-ext-install zip```
   
3. restart php container
   


### nginx config craftCMS
```
server {
    listen       80;
    server_name  localhost;
    root 		 /var/www/craft/web; # project web path
    index 		index.html index.php;
    charset utf-8;

  
	location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    access_log off;
    error_log  /var/www/log/nginx/error.log error;

    sendfile off;

    client_max_body_size 10m;


	gzip              on;
    gzip_http_version 1.0;
    gzip_proxied      any;
    gzip_min_length   500;
    gzip_disable      "MSIE [1-6]\.";
    gzip_types        text/plain text/xml text/css
                      text/comma-separated-values
                      text/javascript
                      application/x-javascript
                      application/javascript
                      application/atom+xml;


    location ~ \.php$ {
        fastcgi_pass   		172.17.0.3:9000; # php  ip 
        fastcgi_param 	 	SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        		fastcgi_params;
		fastcgi_intercept_errors off;
        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;
        fastcgi_read_timeout 300;
    }

	location ~ /\.ht {
        deny all;
    }

}

```

