## Miva & WordPress Hybrids
# Miva is Primary

## About

The file structure above is used to demonstrate how Miva & WordPress can be installed at a site's web root. Miva's URI management and WordPresses Permalinks can be coordinated to work on the same domain.

It just requires updating the `.htaccess` file, and updating WordPress's Site Address Settings.

## Updates

This process essentially works by forcing all traffic to Miva's URI management, *unless*:

* It is an actual file on the server (.css, .js, .jpg, .xml, etc.)
* The URI starts with "wp" (wp-admin, wp-login.php, etc.)
* The URI starts with "blog" (The "sub-directory" we'll use to seperate Miva from WordPress URLs)
* The URI starts with "mm5" (mm5/merchant.mvc, mm5/admin.mvc, mm5/json.mvc, etc.)


### WordPress Site Address

1. In the WordPress Admin, go to the Settings > General page.
2. Change the "Site Address (URL)" to include the "sub-directory" that you have chosen (e.x. from http://www.example.com to http://www.example.com/blog/)

![Image shows screen shot of changing the WordPRess > Settings > General > Site Address (URL) from http://www.example.com/ to http://www.example.com/blog/](wordpress-site-address-settings.jpg)

### .htaccess

Update the existing Miva & Wordpress rule sets to work like this:

```
### Begin - (Custom) Miva Merchant URI Management
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-s
RewriteCond %{REQUEST_URI} !^/wp-.*$
RewriteCond %{REQUEST_URI} !^/blog/.*$
RewriteCond %{REQUEST_URI} !^/mm5/.*$
RewriteRule ^(.*)$ /mm5/uri.mvc? [QSA,L]
### End - (Custom) Miva Merchant URI Management


# BEGIN (Custom) WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END (Custom) WordPress
```