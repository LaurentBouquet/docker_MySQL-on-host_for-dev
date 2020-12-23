# Documentation to start Docker containers with locale MySQL database


## Setting environnement variables

1. copy .env.exemple to .env

2. update .env file, with your variables :

```yaml
DATABASE_ROOT_PASSWORD=secret
DATABASE_NAME=project
DATABASE_USER=project
DATABASE_PASSWORD=dbpassword
```



## Locale database

Create locale MySQL database
with same information as .env file :

```sql
CREATE USER 'project'@'localhost' IDENTIFIED BY 'dbpassword';
CREATE DATABASE project CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
GRANT ALL PRIVILEGES ON project.* TO 'project'@'localhost';
```




## Starting project's containers

docker-compose -p "project" up -d

To enter into PHP container : 
```sh
docker exec -it project-php /bin/sh
```



## Testing project software

1. Open http://localhost:8080 with your web browser




