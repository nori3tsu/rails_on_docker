# Rails on Docker

* Ruby on Rails
* MySQL
* Redis

## Initialization

```
$ docker-compose build
```

## Create New Application

```
$ docker-compose run --rm app rails new . --force --database=mysql --skip-bundle --skip-git
```

Then configure database.yml for Docker.

```
16,18c16,18
<   username: root
<   password:
<   host: localhost
---
>   username: <%= ENV.fetch("MYSQL_USERNAME") %>
>   password: <%= ENV.fetch("MYSQL_PASSWORD") %>
>   host: <%= ENV.fetch("MYSQL_HOST") %>
```

## Run Application

```
$ docker-compose up
```

## Commands

Before executing the command, you need to enter the app container.

```
$ docker-compose exec app bash
```

Initialize the database.

```
root@21d257454c6e:/app# bundle exec rake db:create
root@21d257454c6e:/app# bundle exec rake db:migrate
```
