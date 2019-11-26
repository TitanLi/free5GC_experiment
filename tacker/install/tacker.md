## Create Tacker DB
```shell
CREATE DATABASE tacker;
GRANT ALL PRIVILEGES ON tacker.* TO 'tacker'@'localhost' \
  IDENTIFIED BY 'TACKER_DBPASS';
GRANT ALL PRIVILEGES ON tacker.* TO 'tacker'@'%' \
    IDENTIFIED BY 'TACKER_DBPASS';
```