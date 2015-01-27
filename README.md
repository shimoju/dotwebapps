# dotwebapps

.web/apps

## Requirements

Install the following software:

- Apache (>= 2.4)
- PHP + PHP-FPM
- [Phusion Passenger](https://www.phusionpassenger.com/)

Enable the following Apache modules:

- [mod_proxy](http://httpd.apache.org/docs/current/mod/mod_proxy.html)
- [mod_proxy_fcgi](http://httpd.apache.org/docs/current/mod/mod_proxy_fcgi.html)
- [mod_vhost_alias](http://httpd.apache.org/docs/current/mod/mod_vhost_alias.html)
- [mod_passenger](https://www.phusionpassenger.com/documentation/Users%20guide%20Apache.html)

## Setup

```
git clone https://github.com/shimoju/dotwebapps.git ~/.web
```

Add to the end of `httpd.conf`:

```
Include "/Users/YOURNAME/.web/config/apache/dotwebapps.conf"
```

Edit `~/.web/config/apache/dotwebapps.conf`:

```
# User settings
Define dwa-root "/Users/YOURNAME/.web"
Define dwa-domain loopback.jp
Define dwa-ip 10.0.1.2
Define dwa-default-app-type ruby
Define dwa-php-fpm "fcgi://127.0.0.1:9000"
Define dwa-ruby "/Users/YOURNAME/.rbenv/shims/ruby"
```

Restart Apache.

## Usage

Symlink to `~/.web/apps/`:

```
chmod 755 ~/projects
ln -s ~/projects/ruby-app ~/.web/apps/ruby
ln -s ~/projects/php-app ~/.web/apps/php
```

Access your URL:

```
http://app-name.app-type.your-local-domain/
http://app-name.your-local-domain/ (using default app type)
```

ex)

- [ruby-app.ruby.loopback.jp](http://ruby-app.ruby.loopback.jp/)
  - = [ruby-app.loopback.jp](http://ruby-app.loopback.jp/)
- [php-app.php.loopback.jp](http://php-app.php.loopback.jp/)

Access from another computer on your local network:

```
http://app-name.app-type.your-local-ip.xip.io/
```

ex)

- [ruby-app.ruby.10.0.1.2.xip.io](http://ruby-app.ruby.10.0.1.2.xip.io/)
  - = [ruby-app.10.0.1.2.xip.io](http://ruby-app.10.0.1.2.xip.io/)
- [php-app.php.10.0.1.2.xip.io](http://php-app.php.10.0.1.2.xip.io/)

## License

[MIT](https://github.com/shimoju/dotwebapps/blob/master/LICENSE)

## Author

[Hiroshi Shimoju](https://github.com/shimoju)
