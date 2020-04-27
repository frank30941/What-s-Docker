# Simple example
## Getting start 

``` shell
docker network create net-mysql

docker run --name simple-mysql \
-e MYSQL_ROOT_PASSWORD=root \
-p 3306:3306 \
--network net-mysql \
-d \
--rm \
mysql:5.7.25

docker run --name simple-phpmyadmin \
-e PMA_HOST=simple-mysql \
-p 80:80 \
--network net-mysql \
-d \
--rm \
phpmyadmin/phpmyadmin:latest

docker ps -a;

docker stop simple-mysql simple-phpmyadmin;

docker network rm net-mysql

```
- docker network create XXXX : 創建網路環境
- -e : environment //環境變數
- -p : bind public port // 與實體主機的port 對接 
- --network : 設定在哪個網路上
- -d : detach 背景執行

## docker-compose
### Create a docker-compose.yml
``` yaml
version: "2"
services:
  mysql:
    image: mysql:5.7.25
    container_name: simple-mysql
    restart: always
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: "root"
    networks:
      - net-mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin:latest
    container_name: simple-phpmyadmin
    ports:
      - "80:80"
    environment:
      PMA_HOST: simple-mysql
    networks:
      - net-mysql

networks:
  net-mysql:
```

``` shell
$
docker-compose up
```
