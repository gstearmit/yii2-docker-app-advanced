Docker-compose config for Yii 2 Advanced Project Template
===================================
Yii 2 docker is a configuration for easy deployment and development of Yii 2 Advanced Project Template.

REQUIREMENTS
------------

Docker and Docker compose

INSTALLATION VIA COMPOSER
-------------------------
```
composer create-project --prefer-dist --no-install consultnn/yii2-docker-app-advanced app
```

MANUALLY INSTALLATION
---------------------
Clone this repository
```
git clone https://github.com/consultnn/yii2-docker-app-advanced.git app
```
Change directory
```
cd app
```
Remove git directory
```
rm -rf .git
```
Install Yii 2 Advanced Project Template via composer inside docker container
```
docker-compose run --rm php composer create-project --prefer-dist yiisoft/yii2-app-advanced project
```
Change project directory owner (default root, because process inside container run as root)
```
chown -R $USER:$USER project
```

DIRECTORY STRUCTURE
-------------------
```
docker                          contains docker configuration, build files and logs
    nginx                       nginx docker configuration
    php                         php docker configuration
project                         Yii 2 Advanced Project Template
docker-compose.yml              docker-compose configuration
```


USING
------
For executing commands inside docker container run
~~~
docker-compose run --rm {service} {command}
or, if application already running
docker exec {service} {command}
~~~
For example:
~~~
docker-compose run php composer install
docker exec run php /init
~~~

Start docker containers
~~~
docker-compose up -d
~~~
NOTE: for composer use `--prefer-dist` options, git not installed in php container.
NOTE: inside php container default directory - project

After start check http://127.0.0.1:8090