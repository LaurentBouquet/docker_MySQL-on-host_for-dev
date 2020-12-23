# Documentation to start Docker containers with locale MySQL database



## Setting environnement variables

1. copy .env.exemple to .env

2. update .env file, with your variables :

```yaml
DATABASE_ROOT_PASSWORD=secret
DATABASE_NAME=joliquiz
DATABASE_USER=joliquiz
DATABASE_PASSWORD=dbpassword
```



## Locale database

Create locale MySQL database
with same information as .env file :

```sql
CREATE USER 'joliquiz'@'localhost' IDENTIFIED BY 'dbpassword';
CREATE DATABASE joliquiz CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
GRANT ALL PRIVILEGES ON joliquiz.* TO 'joliquiz'@'localhost';
```




## Clone repository

1. git clone https://github.com/LaurentBouquet/joliquiz.git

2. cd joliquiz

3. copy .env.dist to .env

4. update .env file, with your variables :
```sh
DATABASE_URL=mysql://joliquiz:dbpassword@host.docker.internal:3306/joliquiz
```





## Starting JoliQuiz's containers

docker-compose -p "joliquiz" up -d

To enter into PHP container : 
```sh
docker exec -it joliquiz-php /bin/sh
```

To download and install Composer packages : 
```sh
composer install

```




## Importing fixtures data 

```bash
php bin/console doctrine:migrations:migrate
php bin/console doctrine:fixtures:load
php bin/console server:start
```





## Testing JoliQuiz software

1. Open http://localhost:8080 with your web browser
2. Click on **Login** link



