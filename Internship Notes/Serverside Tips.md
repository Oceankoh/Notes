# Apache

## `.htaccess` file
The .htaccess (Hypertext Access) file is an Apache distributed server configuration file. You can use the .htaccess file to set server configurations for a specific (sub)directory. The .htaccess file can modify various configurations and thus make changes to the website. These changes include authorization, error handling, redirects for specific URLs, user permissions, etc. 

For instance, a `.htaccess` file with the following line allows `.l33t` files to be executed as php. 
```
AddType application/x-httpd-php .l33t
```

# Common Headers 

|Header |Description|
| --- | --- |
|`X-Forwarded-For`|Identifies the originating IP address of a client connecting to a web server through a proxy server|
|`X-Forwarded-Host`|Identifies the original host requested by the client
