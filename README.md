# eZ Docker

This simple project aims to provide a simple setup for eZ Publish 5 dev using docker-compose.

This is a work in progress so feel free to contribute.

## Containers

* Apache-PHP
* MySQL

The Apache-PHP container is linked to the MySQL container so use can access your database using doctrine.

## Usage

1. Clone the repo.
2. Put your eZ Publish files inside /volumes/www/
3. Change the mysql password if needed in /dockerfiles/mysql/Dockerfile
4. If needed, you can change the apache settings (timezone, etc.) in /dockerfiles/apache/Dockerfile
5. Configure the /conf/vhost.conf file as needed. It will automatically be copied to the container.
6. Start the containers :  docker-compose up
7. Connect to the mysql container to create (and import) your database : docker exec -i -t ezdocker_mysql_1 bash
8. Connect to the apache container to generate assets : docker exec -i -t ezdocker_apache_1 bash
9. Access your site using the host name you put in the vhost.conf file
