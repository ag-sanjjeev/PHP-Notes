## &#10162; Configuring Apache Server:
When comes into web development, Configuration is essential and need to adjust server configuration to meet overall project requirements and aspects.

### &#9780; Overview:
1. [Configuration Files](#-configuration-files)
2. [Basic Configuration](#-basic-configuration)
3. [Configuring Virtual Hosts](#-configuring-virtual-hosts)
4. [HTACCESS Configuration](#-htaccess-configuration)
5. [Additional Configuration Options](#-additional-configuration-options)
6. [Key points to remember](#-key-points-to-remember)

### &#10022; Configuration Files:
The primary configuration file for Apache is usually named `httpd.conf` and `httpd-vhosts.conf`. This file contains directives that control various aspects of the server behavior. 

Configuring apache server locally is possible due to full access by the user. How ever, on the web mostly, shared web hosting is used to host multiple websites on single server. Thus it will not allow us to edit those configuration `httpd.conf` and `httpd-vhosts.conf`. 

But apache server gives possibility to configure with certain option through `.htaccess` files. In order to install and use `wordpress`, `laravel` or any other PHP frameworks then it need `.htaccess` to work properly.

### &#10022; Basic Configuration:
From the configuration files, It is possibilities to configure following options of the server.

- `ServerRoot`: It specifies the root directory of the Apache installation.
- `DocumentRoot`: It specifies the document root directory, where website files are located.
- `ServerName`: It sets the server domain name.
- `ErrorLog and CustomLog`: To configure error and access logs to monitor server activity.

```apache
<VirtualHost *:80>
    ServerName example-host.com
    DocumentRoot /var/www/example-host.com

    <Directory "/var/www/example-host.com">
        AllowOverride All
    </Directory>

    ErrorLog "/var/log/apache2/example-host.com-error.log"
    CustomLog "/var/log/apache2/example-host.com-access.log" combined
</VirtualHost>
```

### &#10022; Configuring Virtual Hosts:
To configure multiple virtual hosts to serve different websites from the same server. Each virtual host has own DocumentRoot, ServerName, and other settings.

*Example:*
```apache
<VirtualHost *:80>
   ServerName example-host.com
   DocumentRoot /var/www/example-host.com
</VirtualHost>

<VirtualHost *:80>
   ServerName another-host.com
   DocumentRoot /var/www/another-host.com
</VirtualHost>
```

### &#10022; HTACCESS Configuration:
Shared hosting environments restricts direct access to configuration files `httpd.conf` and `httpd-vhosts.conf`. These configuration affects overall server behavior and primarily due to security concerns and resource management. However, most of shared hosting environments allow their own configuration through `.htaccess` files.

In order to allow `.htaccess` file on specific virtual host to work properly, then it need to edit configuration for virtual host and add `AllowOverride All` property for the particular directory of virtual host. That tells `.htaccess` can override the properties for current virtual host directory.

```apache
<VirtualHost *:80>
    ServerName localhost
    DocumentRoot "/C:/xampp/htdocs/site1"

    <Directory "/C:/xampp/htdocs/site1">
        Require all granted
        AllowOverride All
    </Directory>
</VirtualHost> 
```

### &#10022; Additional Configuration Options:
- Directory Index: It specifies the default document to serve when a directory is requested.
```htaccess
DirectoryIndex index.php index.html
```

- Error Documents: It customizes error pages for specific HTTP status codes.
```htaccess
ErrorDocument 404 /error.html
```

- Rewrite Rules: It allows to rewrite URLs. It makes more user-friendly and SEO-friendly.
```htaccess
RewriteEngine On
RewriteRule ^articles/([^/]+)$ blog/articles.php?post=$1 [L]
```

- File and Directory Permissions: It controls access to files and directories.   
```htaccess
<Directory /var/www/html/protected>
   Require valid-user
</Directory>
```

- MIME Types: It specifies the MIME type for different file extensions.   
```htaccess
AddType application/x-httpd-php .php
```

- IP-Based Access Control: It restrict access to specific IP addresses or ranges.
```htaccess
<Limit GET POST>
    Order deny,allow
    Deny from all
    Allow from 192.168.1.0/24
</Limit>
```

**Other Options:**
- Directory Directives: It sets control access permissions for files such as index files, and other settings for specific directories.
- FileType-Specific Directives: It controls Apache to handles different file types.
- Security Headers: Implement security headers to protect website.
- Modularity: Extend the functionalities by using Apache modules such as `mod_rewrite` for URL rewriting and `mod_ssl` for SSL/TLS.

*Note:* To refer useful and variety of `.htaccess` code snippets from this [third-party repository](https://github.com/phanan/htaccess)

### &#10022; Key points to remember:
- Always test configurations before implement to the production server.
- Check with the official documentation and get expert advices.
- Use a configuration management tool to simplify deployment and management.

---
[&#8682; To Top](#-configuring-apache-server)

[&#10094; Previous Topic](./remember-logged-in-user.md) &emsp; [Next Topic &#10095;](./web-frameworks.md)

[&#8962; Goto Home Page](../README.md)