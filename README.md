# M1 Docker

## Quick start

    git clone git@github.com:DominicWatts/docker-magento.git ./

    mkdir magento

    mkdir mysql

    docker-compose up -d

### Magento install

Files go into ./magento

### Admin password

admin / HxH5F6VtkcBN7zkB

### Fetch files from git

Swap `1.9.4.3` for release version

    cd magento

    curl -LJO https://github.com/OpenMage/magento-mirror/archive/1.9.4.3.tar.gz

    tar -zxvf magento-mirror-1.9.4.3.tar.gz magento-mirror-1.9.4.3

    mv magento-mirror-1.9.4.3/* ./

    rm magento-mirror-1.9.4.3 -rf

    rm magento-mirror-1.9.4.3.tar.gz

### Setup notes

#### Magerun

    docker-compose run --rm cli magerun

    docker-compose run --rm cli magerun cache:clean

#### phpmyadmin

http://magento.docker:8000/

#### Email

##### Magento Extension

    https://github.com/aschroder/Magento-SMTP-Pro-Email-Extension

##### MailHog

    http://magento.docker:8025

##### Configuration

    host: mail
    port: 1025
    protocol: none
    authentication: plain
    username/password: [blank]
