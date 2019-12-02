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
## Installation

### Install by UI
- Video tutorial: https://www.youtube.com/watch?v=PNBeHXDpinI&feature=youtu.be

* Run `composer install` to download vendor packages

* Create `.env` file from `.env-example` and update your configuration

* Run `php artisan migrate` to create database structure with no sample data or import default database from `database.sql` if you need sample data.

* Run `php artisan cms:user:create` to create admin user

* Run `php artisan vendor:publish --tag=cms-public --force`

* Run `php artisan cms:theme:activate flex-home`

* Run `php artisan cms:theme:assets:publish`

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
