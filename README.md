# M1 Docker

## Quick start

    git clone git@github.com:DominicWatts/docker-magento.git ./

    mkdir magento

    mkdir mysql

    docker-compose up -d
    
### Magento install

Files go into ./magento

#### Quickstart : Hypernode mirror

Inside ./magento

    wget -qO- https://magento.mirror.hypernode.com/releases/magento1-latest.tar.gz | tar xfz -

or

    wget -qO- https://magento.mirror.hypernode.com/releases/magento-1.9.4.4.tar.gz | tar xfz -

#### Quickstart : Magento LTS

Inside ./

    composer.json
    
```json
{
    "require": {
        "aydin-hassan/magento-core-composer-installer": "*",
        "openmage/magento-lts": "19.4.6"
    },
    "extra": {
        "magento-core-package-type": "magento-source",
        "magento-root-dir": "magento"
    }
}
```

    composer install

#### Quickstart : OpenMage git

Swap `1.9.4.3` for release version

    cd magento

    curl -LJO https://github.com/OpenMage/magento-mirror/archive/1.9.4.3.tar.gz

    tar -zxvf magento-mirror-1.9.4.3.tar.gz magento-mirror-1.9.4.3

    mv magento-mirror-1.9.4.3/* ./

    rm magento-mirror-1.9.4.3 -rf

    rm magento-mirror-1.9.4.3.tar.gz

### Database Credentials

    Host: db
    User: magento
    Password: magento
    Database: magento

### DB Restore

Dump goes into ./magento

    docker-compose run --rm cli mysql --init-command="SET SESSION FOREIGN_KEY_CHECKS=0;" -u magento -pmagento -h db magento

    mysql> use magento;

    mysql> SET autocommit=0 ; SOURCE dump.sql ; COMMIT ;

### Example admin password

admin / HxH5F6VtkcBN7zkB

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
