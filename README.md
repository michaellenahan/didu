didu

"drupal-ich, drupal-du"

A community building website.

INSTRUCTIONS

-- tested on ubuntu 14.04, should work on any system though
-- install composer globally https://getcomposer.org/doc/00-intro.md
-- install drupal console using these instructions: https://hechoendrupal.gitbooks.io/drupal-console/content/using/installer.html
-- download drupal using these instructions: https://github.com/drupal-composer/drupal-project#usage

-- workspace is where i put my web projects, you will probably use another folder

➜  workspace  composer create-project drupal-composer/drupal-project:8.x-dev didu --stability dev --no-interaction
➜  workspace  cd didu
➜  didu  git init
Initialized empty Git repository in /home/michael/workspace/didu/.git/
➜  didu git:(master) ✗ git add .
➜  didu git:(master) ✗ git commit -m'composer create-project drupal-composer/drupal-project:8.x-dev didu --stability dev --no-interaction'
[master (root-commit) 37e1afd] composer create-project drupal-composer/drupal-project:8.x-dev didu --stability dev --no-interaction

-- create a database didu, with user didu password didu
-- create an apache config
-- here's an example that works on ubuntu 14.04:
<VirtualHost *:80>
        ServerAlias didu.local
        DocumentRoot /home/michael/workspace/didu/web
        <Directory "/home/michael/workspace/didu/web">
                Options FollowSymLinks
                AllowOverride All
                Require all granted
        </Directory>
</VirtualHost>

-- check in your browser -- when you go to http://didu.local you should get the drupal installation screen

-- install drupal
➜  web git:(master) drush si --db-url=mysql://didu:didu@localhost/didu

-- change admin password
➜  web git:(master) ✗ drush upwd admin --password=admin

-- now you should be able to go to http://didu.local and log in as user admin password admin

-- set 
➜  didu git:(master) drupal list | grep site

