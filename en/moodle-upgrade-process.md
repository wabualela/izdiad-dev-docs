# moodle update/upgrade process
## intial configuration
- enabled moodle maintenance mode 
- take snapshot from digialocean
## backup
- backup moodledata directory and save it locally.
- backup database 
```
    mysqldump -u [database_username] -p -v [database_name] >  database_name.sql
    or 
    mysqldump -u [database_username] -p -v [database_name] | gzip >  database_name.sql.gz
```
- check your database version 
- upgrade server packages 
```
    sudo apt update 
    sudo apt upgrade -y
```
## database upgrade
- after backup your database remove old database version
```
    sudo apt remove mariadb-*
```
-- update server repo to read the latest database version
```
    wget https://downloads.mariadb.com/MariaDB/mariadb_repo_setup
    
    echo "367a80b01083c34899958cdd62525104a3de6069161d309039e84048d89ee98b mariadb_repo_setup" | sha256sum -c -
    
    chmod +x mariadb_repo_setup
    sudo ./mariadb_repo_setup --mariadb-server-version="mariadb-10.5"
    
    sudo apt update
```
--- install the new verison    
    ```
    sudo apt install mariadb-server
```
- after complete the bakcup process nagivate to your moodle intallation directory and run
```
    git pull
```
- if moodle version need to upgrade (i.e. 3.11 to 4.1.1) 
```
    git checkout v4.1.1
```
- clean up after you. 
