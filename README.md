# how-to-deploy-laravel-vue3-to-ubuntu

## A Step-by-Step Guide to Setting Up Your GitHub Account on Ubuntu
- sudo apt update
- sudo apt install git
- git config --global user.name "<Your Name>"
- git config --global user.email "<your-email@example.com>"
- REFERENCE: https://medium.com/@ak4634/a-step-by-step-guide-to-setting-up-your-github-account-on-ubuntu-69143502b7d0

## How to clone GIT Repository
- go to directory /var/www
- git clone https://github.com/username/repository-name

## Run npm install
## Run composer install
## Run npm run build
## Setup .env file
## Run php artisan migrate --seeder

## Create Apache2 Virtual Host
- cd etc/apache2/sites-available
- sudo nano project_name.conf / touch project_name.conf
- PASTE THIS:
  
<VirtualHost *:80>
        DocumentRoot /var/www/project_name/public
        ServerPath /project_name/public
        ServerName domain_name.com
        <Directory "/var/www/project_name/public">
                Options Indexes Followsymlinks
                AllowOverride All
                Require all granted
        </Directory>
RewriteEngine on
RewriteCond %{SERVER_NAME} =stage2.tbpo.net
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

- CTRL+X to exit
- CTRL+Y to save

## Enabling added Virtual Host
- sudo a2ensite project_name.conf
- sudo a2enmod rewrite

## Adding SSL Certificate
- REFERENCE: https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu
