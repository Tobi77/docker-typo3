# TYPO3 on Docker

This setup provides a running TYPO3 v8.7 instance with xdebug in development context. 

    docker-compose up --build -d 
    
    docker-compose up -d



### Database
Use the following credentials to connect to the database via your DB client.

Username: root \
Password: root \
Host: db \
Port: 3306 


#### Included settings

- SSL
- xdebug
- apache vhost
- mailhog

#### Todo

- git


#### Gasmask 

    127.0.0.1 www.test.local

#### xdebug

xdebug is running on Port 9000 with the IDEkey PHPSTORM.


#### MailHog
Start using MailHog via http://www.test.local:8025/

To use it, set the following settings in LocalConfiguration

    [MAIL][transport] = smtp
    [MAIL][transport_smtp_server] = mail:1025
