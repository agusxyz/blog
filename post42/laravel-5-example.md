---
title: 'Laravel 5 example'
date: 2017-03-21T02:41:00.000-07:00
draft: false
tags : [Laravel]
---

Laravel 5 example
-----------------

  
For Laravel 5.3 improved version look at [this repository](https://github.com/bestmomo/laravel5-3-example).  
  
**Laravel 5 example** is a tutorial application for Laravel 5.2 (in french [there](http://laravel.sillo.org/laravel-5/)).  

### [](https://github.com/bestmomo/laravel5-example#installation)Installation

  

  

  
*   `git clone https://github.com/bestmomo/laravel5-example.git projectname`
  
*   `cd projectname`
  
*   `composer install`
  
*   `php artisan key:generate`
  
*   Create a database and inform _.env_
  
*   `php artisan migrate --seed` to create and populate tables
  
*   Inform _config/mail.php_ for email sends
  
*   `php artisan vendor:publish` to publish filemanager
  
*   `php artisan serve` to start the app on [http://localhost:8000/](http://localhost:8000/)
  

  

  
  
\[java\]composer create-project laravel/laravel laravelapp --prefer-dist\[/java\]  
  

  
Another cool way to install it is to upload [this package](http://laravel.sillo.org/tuto/installable.zip), unpack it in your server folder, and just launch it and follow the installation windows. It has been created with my [laravel installer package](https://github.com/bestmomo/laravel-installer). Anyway you'll have to set the email configuration.  

### [](https://github.com/bestmomo/laravel5-example#nitrous-quickstart)Nitrous Quickstart

  
Create a free development environment for this Laravel 5 example project in the cloud on [Nitrous.io](https://www.nitrous.io/) by clicking the button below.  
  
[![Nitrous Quickstart](https://camo.githubusercontent.com/8955893258d2c3d36b126e7ecb9cf79c0cf4b1ee/68747470733a2f2f6e6974726f75732d696d6167652d69636f6e732e73332e616d617a6f6e6177732e636f6d2f717569636b73746172742e706e67)](https://www.nitrous.io/quickstart)  
  
In the IDE, start Laravel 5 Example via `Run > Start Laravel 5 Example` and access your site via `Preview > 8000`.  

### [](https://github.com/bestmomo/laravel5-example#include)Include

  

  
*   [HTML5 Boilerplate](http://html5boilerplate.com/) for front architecture
  
*   [Bootstrap](http://getbootstrap.com/) for CSS and jQuery plugins
  
*   [Font Awesome](http://fortawesome.github.io/Font-Awesome) for the nice icons
  
*   [Highlight.js](https://highlightjs.org/) for highlighting code
  
*   [Startbootstrap](http://startbootstrap.com/) for the free templates
  
*   [CKEditor](http://ckeditor.com/) the great editor
  
*   [Filemanager](https://github.com/simogeo/Filemanager) the easy file manager
  

  

### [](https://github.com/bestmomo/laravel5-example#features)Features

  

  
*   Home page
  
*   Custom Error Page 404
  
*   Authentication (registration, login, logout, password reset, mail confirmation, throttle)
  
*   Users roles : administrator (all access), redactor (create and edit post, upload and use medias in personnal directory), and user (create comment in blog)
  
*   Blog with comments
  
*   Search in posts
  
*   Tags on posts
  
*   Contact us page
  
*   Admin dashboard with new messages, users, posts and comments
  
*   Users admin (roles filter, show, edit, delete, create)
  
*   Messages admin
  
*   Posts admin (list with dynamic order, show, edit, delete, create)
  
*   Medias gestion
  
*   Localisation
  

  

### [](https://github.com/bestmomo/laravel5-example#packages-included)Packages included

  

  
*   laravelcollective/html
  
*   bestmomo/filemanager
  

  

### [](https://github.com/bestmomo/laravel5-example#tricks)Tricks

  
To test application the database is seeding with users :  

  
*   Administrator : email = [admin@la.fr](mailto:admin@la.fr), password = admin
  
*   Redactor : email = [redac@la.fr](mailto:redac@la.fr), password = redac
  
*   User : email = [walker@la.fr](mailto:walker@la.fr), password = walker
  
*   User : email = [slacker@la.fr](mailto:slacker@la.fr), password = slacker