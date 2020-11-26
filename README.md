# Heroku PHP deploy

> ## The following process install has been tested on a LIVE USB UBUNTU distribution

### Install dependencies

```sh
sudo apt install git
sudo apt install php7.4
```

### Install Composer

- for windows [composer.exe](https://getcomposer.org/Composer-Setup.exe)

- for unix users

```sh
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
sudo mv composer.phar /usr/local/bin/composer
``` 

### Configuration files required for deploy

> Create a new directory on your machine and initialize a git repository in it. Next add the following files.

- Create a `composer.json` file with the following content:

```js
{
  "require": {
    "php": "~7.4"
  }
}
```

- If you need the PHP errors to be displayed, create a `.user.ini` file with the following content:

```sh
display_errors = on
log_errors = on
```

- Create a `index.php` file with the following content:

```php
<?php phpinfo();
```

- Create a `.gitignore` file with the following content: `vendor/`

- Run `composer update`
- Finally execute your local git commands to push your modifications to your corresponding github repository

### Setup a MySQL database with heroku-cli

>ClearDB addon is free with the `Ignite`  plan

- Install the heroku CLI

`curl https://cli-assets.heroku.com/install-ubuntu.sh | sh`

- Login to your account

`heroku login`

- Install the add-on

`heroku addons:add cleardb:ignite -a YOUR_HEROKU_APP_NAME`

- Retrieve your credentials

Go to the [ClearDB dashboard](https://www.cleardb.com/dashboard) then click on the database and "security" tab
