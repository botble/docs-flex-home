# Introduction
- [Requirement](#requirement)
- [Installation](#installation)
- [Note](#note)

<a name="requirement"></a>
## Requirement

**We recommend to use MAMP PRO (https://www.mamp.info/en/) instead of Xampp to create develop environment. With MAMP, you can easy to add/manage virtual domain like flex-home.local.**

- Apache, nginx, or another compatible web server.
- PHP >= 7.2 >> Higher
- MySQL Database server
- PDO PHP Extension
- OpenSSL PHP Extension
- Mbstring PHP Extension
- Exif PHP Extension
- Fileinfo Extension
- XML PHP Extension
- Ctype PHP Extension
- JSON PHP Extension
- Tokenizer PHP Extension
- Module Re_write server
- PHP_CURL Module Enable

>  {warning} On this project, I use the latest Laravel version (currently 6.x). Please go to [Laravel documentation page](https://laravel.com/docs) for more information.

<a name="installation"></a>
## Install on hosting

- Upload all files into `public_html`.
- Create a database and import data from `database.sql` (it's located in source code).
- Create `.env` from `.env.example` and update your database information
- Config for media:
    + If your hosting support SSH, you just need to cd to `public_html` and run command `php artisan storage:link`
    + If your hosting doesn't support SSH. You have to open file `config/filesystem.php`
                                           
       Then change
       
       ```php
       'public' => [
           'driver' => 'local',
           'root' => storage_path('app/public'),
           'url' => env('APP_URL').'/storage',
           'visibility' => 'public',
       ],
       ```
       
       to
       
       ```php
       'public' => [
           'driver' => 'local',
           'root' => public_path('storage'),
           'url' => env('APP_URL').'/storage',
           'visibility' => 'public',
       ],
       ```
      
       Copy all files from `/storage/app/public` to `public/storage`.


## Install locally or in VPS

### Install by UI
Installation steps:

- Access to `your-domain.com/install` to start install Flex Home.
![Welcome](https://botble.com/storage/docs/install-ul/1.png)

- Check server's requirements
![Check requirements](https://botble.com/storage/docs/install-ul/2.png)

- Config database information
![Config database](https://botble.com/storage/docs/install-ul/3.png)

- Create admin account
![Create admin account](https://botble.com/storage/docs/install-ul/5.png)

- Finish
![Finish](https://botble.com/storage/docs/install-ul/6.png)

> {note} After finished installation, please login to admin (/admin) and go to Plugins then activate all plugins to use. 

- Video tutorial: https://www.youtube.com/watch?v=PNBeHXDpinI&feature=youtu.be

Note: If you install it locally, you can run `php artisan serve` to start server then access to `http://localhost:8000/install` to start install by UI.

### Install manual
* Run `composer install` to download vendor packages

* Create `.env` file from `.env-example` and update your configuration

* Run `php artisan migrate` to create database structure with no sample data or import default database from `database.sql` if you need sample data.

* Run `php artisan cms:user:create` to create admin user

* Run `php artisan vendor:publish --tag=cms-public --force`

* Run `php artisan cms:theme:activate flex-home`

* This project requires some plugins. Run following commands to activate it.

```
php artisan cms:plugin:activate real-estate
php artisan cms:plugin:activate location
php artisan cms:plugin:activate blog
php artisan cms:plugin:activate language
```

* Run `php artisan storage:link`

Note: If you can't run `php artisan storage:link` (some hosting doesn't support it), you can change config
in `/config/filesystems.php` like this https://prnt.sc/pn50dc then move all uploaded file from `/storage/app/public` to `/public/storage`.

* Run the first test with command `php artisan serve`. Open `http://localhost:8000`, you should see home page of Botble CMS


**If you need sample data, you can import it from `database.sql`**

**FlexHome should run on a virtual host. Create a virtual host like cms.local to run FlexHome. Follow these steps to see how to config virtual host: [Setup virtual host](/flex-home/3.5/virtualhost).** 

<a name="note"></a>
## Note

This site can only be run at domain name, not folder link.

On your localhost, setting virtual host. Something like `http://flex-home.local` is ok.

Cannot use as `http://localhost/flex-home/...`.

Please remove `public` in your domain also, you can point your domain to `public` folder

or use `.httaccess` (https://stackoverflow.com/questions/23837933/how-can-i-remove-public-index-php-in-the-url-generated-laravel)

Follow these steps to see how to config virtual host: [Setup virtual host](/cms/4.0/virtualhost).

Well done! Now, you can login to the dashboard by access to your_domain_site/admin.

    Username: botble
    Password: 159357

Enjoy!
