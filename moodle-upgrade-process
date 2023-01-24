# upgrade moodle droplet
- enabled moodle maintenance mode 
- take snapshot from digialocean
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
- if database version need upgrade 
```
    sudo apt remove mariadb-*
    wget https://downloads.mariadb.com/MariaDB/mariadb_repo_setup
    echo "367a80b01083c34899958cdd62525104a3de6069161d309039e84048d89ee98b mariadb_repo_setup" | sha256sum -c -
    chmod +x mariadb_repo_setup
    sudo ./mariadb_repo_setup --mariadb-server-version="mariadb-10.5"
    sudo apt update
    sudo apt install mariadb-server
```
- nagivate to your moodle intallation directory and run
```
    git pull
```
- clean up after you. 
