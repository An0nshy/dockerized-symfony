# dockerized-symfony

Clean Setup for a fresh Symfony project.
Symfony version : 5.0 website-skeleton

Start the project with docker-compose up.

Parameter: 

- Symfony: localhost:8080
- Database: localhost:3306
- Phpmyadmin: localhost:8081

If you want to change the Enviorment you can change the settings in the .env file in the root directory.

How to use:

- docker exec -it webserver_php_1 bash
- .bin/console [command]

Or you have composer localy installed.

- go/to/your/DockerContainer
- ./bin/console [command]


In case u get a permission erros run add the web_data folder to the www-data group or use chmod.

- chown -R www-data web_data/
