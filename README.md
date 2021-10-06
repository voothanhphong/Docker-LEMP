# VooThanhDock

Can copy file in bin to /usr/local/bin

## Setup New Project
```setup-project```

Then the command will prompt you to input some information as below:
 - Project path root: 
 - Own Group: group run code. Ex: www-data
 - Git Url: git url of your project. Ex: git@github.com:voothanhphong/Docker-LEMP.git.
 - Branch: git branch you want to use. Ex: master.
 - auth.json: Path of auth.json
 - Database: Path of sql file
 - Base Url: The base url you want to use on your local.
 - Use HTTPS: true/false
 - Is Magento Project: true/false
 - PHP Version: support 7.0 > 7.4
 - Mysql Image: Ex: mysql:5.7

## Useful commands
- `bin/init-doco`: Init docker-compose file.
- `bin/doco`: docker-compose alias.
- `bin/setup-project`: Setup new project.
- `bin/composer`: composer command on php service. (Ex: composer install).
- `bin/php-service`: Docker compose php service alias (docker-compose exec php ...).
- `bin/php-enable`: Enable php module(s).
- `bin/php-disable`: Disable php module(s).
- `bin/pconfig`: Update PHP config on `/usr/local/etc/php/conf.d/zz-docker.ini` (Ex: php-config max_input_vars=100000 memory_limit=8G).
- `bin/ppool`: Update FPM pool config on `/usr/local/etc/php-fpm.d/zz-docker.conf` (Ex: php-pool pm.max_children=40).
- `bin/php`: PHP command on php service (Ex: php -v).
- `bin/redis-cli`: redis-cli command on redis service.
- `bin/mgt`: Magento n98 (Ex: mgt cache:flush).
- `bin/magento`: Run the Magento CLI (Ex: magento cache:flush).
- `bin/init-magento-env`: Init magento env.php file.
- `bin/mysql-import`: Import database.
- `bin/permission`: Fix permission.
- `bin/remove-trash-container`: Remove docker container (remove-trash-container [<exclue name prefix>])
- `bin/clean-docker-volume`: Remove docker volume (clean-docker-volume [<exclue name prefix>])

## Email / Mailhog
View emails sent locally through Mailhog by visiting http://localhost:8025

## Elastic Search

You can access elastic search index via: http://localhost:9200/.

## RabbitMQ
You can access via: http://localhost:15672 . Default user/pass: guest/guest.

## Config

### Nginx
- NGINX_CONFIG
    + Update custom config for nginx
    + Syntax: key=value
    + The key-value pairs ​​are separated by space or new line if using sample file.
- SERVER_NAME
    + Global server name on vhost.
- PHP_SERVICE
    + PHP service name on docker-compose (defaul: php)
- PHP_PORT
    + PHP port on php service. (default: 9000)
- IS_HTTPS
    + Value: true \ false
    + Whether to use https or not
- IS_MAGENTO
    + Value: true \ false
    + Is project magento
- IS_MAGENTO_MULTI
    + Value: true \ false
    + Is magento multi store
    + Only work if is_magento = true
- MAGENTO_MODE
    + Value: developer \ default \ production
    + Magento mode running
    + Only work with magento multi store
- MAGENTO_RUN_TYPE
    + Value: store \ website
    + Magento multi store type
    + Only work with magento multi store
- MAGENTO_MULTI_SITES= # server_name1=store_code1 or website_code1;server_name2=store_code2 or website_code2 ...
    + Syntax: server_name=code
    + Code = store code or website code
    + The server_name-code pairs ​​are separated by ;
    
