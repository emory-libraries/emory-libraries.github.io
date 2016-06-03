---
layout: post
title: Piwik Setup and Configuration Notes  
tags: 
  - jekyll
authors:
    - yang_li
---

# Background


> Piwik is a free and open source web analytics application written by a team of international developers that runs on a PHP/MySQL webserver. It tracks online visits to one or more websites and displays reports on these visits for analysis. As of September 2015, Piwik was used by nearly 900 thousand websites,[1] or 1.3% of all websites,[2] and has been translated to more than 45 languages.[3] New versions are regularly released every few weeks.[4]


Above is copied from Wikipedia about Piwik. In simple words it's Google Analytics open source version.


# Piwik Setup

* Go to the [official guide](https://piwik.org/docs/installation/#getting-started)
* `wget` the zip and extract, you will get a folder called `piwik`
* Next we'd need to let nginx or your web server serve this site with the help of PHP because piwik is a PHP based application

## Install PHP and nginx
* [Guide on how to configure nginx to work with PHP](http://askubuntu.com/questions/134666/what-is-the-easiest-way-to-enable-php-on-nginx)

* (from the guide) if you don't have try these: `sudo apt-get install php5-common php5-cli php5-fpm`

* Then modify the default nginx profile to adapt to the php app piwik

* For simple security we can put apache password protection around the site. Also you should be using a secure password too

* Restart nginx and if it fails check the `error.log` in `/var/log/nginx/`

* If the directory doesn't exist you should try creating the nginx in the log and assign appropriate permissions so that nginx can write to it.

* Now if you navigate to the piwik URI and check the UI, you might either see the welcome page or error messages. For me the permission is not assigned write so that the `root/tmp` folder is not writeable.

* Fixed by temporarily assigning `777` to the folder

* If you see this error below

> error
> Piwik requires either the mysqli extension or both the PDO and pdo_mysql extensions.


* try adding one more to the box:
`apt-get install php5-mysql`

* Now we have a warning:

> GET request to piwik.php failed. Try whitelisting this URL from HTTP Authentication and disable mod_security (you may have to ask your webhost). For more information about the error, check your web server error log file.


* Well it's actually just missing a file so:
`touch  /opt/Source/piwik/config/config.ini.php`

> Error while trying to connect to the database server: SQLSTATE[HY000] [2003] Can't connect to MySQL server on '127.0.0.1' (111)

## Database connection
* Turns out that the hostname needs to be `localhost` as opposed to `127.0.0.1`
* Once we have the piwik running we can test

## Geo referencing add-on

* Piwik requires the package php5-gd and if you don't GD > 2.x + Freetype (graphics) `sudo apt-get install php5-gd`
