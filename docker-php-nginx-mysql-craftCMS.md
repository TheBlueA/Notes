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
   
