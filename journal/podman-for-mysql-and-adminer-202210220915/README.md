# Podman with Mariadb and Adminer in MacOS

...first things first. 

**Enable cookies in your browser.**

## Podman

I found that alpine will do just absolutely fine:

`podman machine init alpine`

`podman machine start | stop alpine`

then if you want to remove:

`podman machine rm alpine`

## Setup MariaDB and Adminer

url: http://0.0.0.0:8082

```
# cleanup
podman pod stop mdb
podman pod rm mdb
podman stop mariadb adminer
podman rm mariadb adminer

# startup a pod
podman pod create \
  --name mdb \
  -p 8082:8080 \
  -p 3306:3306

# setup mariadb
podman run -d \
  --name mariadb \
  --pod mdb \
  -e MYSQL_ROOT_PASSWORD='pass' \
  -e MYSQL_USER=sonny \
  -e MYSQL_PASSWORD='crockett' \
  -e MYSQL_DATABASE=vice \
  mariadb

# setup adminer
podman run -d \
  --name adminer \
  --pod mdb \
  -e ADMINER_DEFAULT_SERVER=mariadb \
  adminer

```
🔗 [gist](https://gist.github.com/unamatasanatarai/dde903920679783d03ff8311203a389e)

## Enter the container

from inside the container

```
podman exec -it mariadb /bin/bash
mysql -uroot -pless
```

from your OS

```
mysql -uroot -pless -h0.0.0.0
```
