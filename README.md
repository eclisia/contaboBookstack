# ContaboBookstack
## Disclaimer
This repository is the configuration for the usage of Bookstack docker instance.
This project if forked from the excellent [https://hub.docker.com/r/linuxserver/bookstack](https://hub.docker.com/r/linuxserver/bookstack)

## Installation guide
### Prerequisite
To have a Centos server with docker fully configured and access to Internet
### Docker-compose installation
This relies on the use of Docker-compose through a **docker-compose.yml** file.
Download this file in the server and configure the parameter as needed.
## Running
TBD
## Backup and Restore
The backup and restore process relies on the official process from the [Bookstack](https://www.bookstackapp.com/docs/admin/backup-restore/).
Please find hereunder the adaptation of the procedure **to be compliant with docker usage.**
Additionnal information can be found [here](https://knoats.com/books/bookstack/page/backup-bookstack-using-docker)
### Database Backup
```sh
docker exec -it bookstack_db  /bin/bash -c 'mysqldump -u bookstack -pSpieSpie06 bookstackapp > /config/backup.sql'
```
Don't forget to adapt to your case :
```sh
docker exec -it your_docker_name  /bin/bash -c 'mysqldump -u your_sql_username -pYoupassword_sql you_sql_db_name > /config/backup.sql'
```
### Datas backup
In the same way, the data can be backup with :

```sh
docker exec -it bookstack /bin/bash -c 'tar -czvf bookstack-files-backup.tar.gz /var/www/html/.env /var/www/html/public/uploads /var/www/html/storage/uploads' 
```
Then, you have to cp the archive file outside the container. For instance hereafter you copy the file in the current dir.
```sh
docker cp bookstack:bookstack-files-backup.tar.gz .
 ```
### Restore
TBD 


