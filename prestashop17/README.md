# prestashop
## add host presta in your host file
```
127.0.0.1       presta
```
## using docker compose
```shell
docker-compose up
# In background with d option
docker-compose up -d
docker-compose stop
```
## manual
```shell
docker run -ti --name some-prestashop --network prestashop-net -e DB_SERVER=some-mysql -e PS_DOMAIN=192.168.0.142:8080 -e PS_SHOP_URL=192.168.0.142:8080 -p 8080:80 --volume /home/$USER/workspace/containers_storage/prestashop:/var/www/html -d prestashop/prestashop
docker run -ti --name some-mysql --network prestashop-net -e MYSQL_ROOT_PASSWORD=admin -p 3307:3306 --volume /home/$USER/workspace/containers_storage/mysql:/var/lib/mysql -d mysql:5.7
# Access to prestashop container
docker exec -ti some-prestashop bash
# Print log stream
docker logs -f some-mysql
# Create new image of existing container
docker commit some-prestashop new-some-prestashop
```
