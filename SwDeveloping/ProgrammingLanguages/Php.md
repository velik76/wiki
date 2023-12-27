# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Show installed modules](#show-installed-modules)
  - [Debugging](#debugging)

## Show installed modules

```bash
php -m
```

## Debugging

Can check the /var/log/apache2/error.log file and in php print out with error_log(), for example:

error_log("Sergey. Value: " . $value)

rrd in PHP

1. Install:

```bash
sudo apt install librrd-dev php-dev php-pear
```

2. May be need to config http-proxy with

```bash
pear config-set http_proxy localhost:3128
```

3. Install rrd extension for php with:

```bash
sudo pecl install rrd
```

4. Can use to get some info the

```bash
php-config
```

and

```bash
pecl list
```

5. In /etc/php/7.2/apache/php.ini/ insert the extension=rrd.so
6. Restart apache2

