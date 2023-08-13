Что не фурычит PHP на докере((
==============================

Проблема
--------

Проблема заключается в ошибке 

```
temp-php-into-docker-php-1    
| [13-Aug-2023 14:07:38] WARNING: [pool www] child 7 said into stderr: "NOTICE: 
Access to the script '/var/www/php/index.phtml' has been denied (see security.limit_extensions)"

temp-php-into-docker-nginx-1  
| 2023/08/13 14:07:38 [error] 22#22: *1 FastCGI sent in stderr: "Access to the script '/var/www/php/index.phtml' 
has been denied (see security.limit_extensions)" while reading response header from upstream, client: 172.21.0.1, 
server: , request: "GET / HTTP/1.1", upstream: "fastcgi://172.21.0.2:9000", host: "localhost:8080"
```

По сути проблема в том, что никак не получается настроить опцию `security.limit_extensions`.
Эта опция вроде как прописана в файле `.docker/php/conf.d/php.ini`. Этот файл вроде как подключается.
Это можно проверить зайдя на страницу http://localhost:8080/phpinfo.php

Вопрос, как правильно подключить `php.ini` и настроить опцию `security.limit_extensions`?

Требуется
---------

Докер  
Git  

Для воспроизведения дефекта
---------------------------

Клонируйте репо:

```
git clone git@github.com:khusamov/temp-php-into-docker.git
git clone https://github.com/khusamov/temp-php-into-docker.git
```

Затем поднимите контейнеры:

```
docker compose up
```

Для проверки приготовлены две страницы:

http://localhost:8080  
http://localhost:8080/phpinfo.php  