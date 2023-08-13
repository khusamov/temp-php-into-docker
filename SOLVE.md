Решение дефекта
===============

Решение дефекта заключается в замене строки в файле `docker-compose.yaml`:

```
./.docker/php/conf.d:/usr/local/etc/php/custom.d
```
на

```
- ./.docker/php/conf.d/php.ini:/usr/local/etc/php-fpm.d/www2.conf
```