# Larinfo

[![Build Status](https://travis-ci.org/matriphe/larinfo.svg?branch=master)](https://travis-ci.org/matriphe/larinfo)
[![Total Download](https://img.shields.io/packagist/dt/matriphe/larinfo.svg)](https://packagist.org/packages/matriphe/larinfo)
[![Latest Stable Version](https://img.shields.io/packagist/v/matriphe/larinfo.svg)](https://packagist.org/packages/matriphe/larinfo)

Larinfo provide system information for Laravel 5.x application. It show IP address information for host and client, server software versions, and hardware information.

## Installation

To install using [Composer](https://getcomposer.org/), just run this command below.

```bash
composer require matriphe/larinfo
```

Open the `config/app.php` and add this line in `providers` section.

```php
Matriphe\Larinfo\LarinfoServiceProvider::class,
```

Still on `config/app.php` file, add this line in `aliases` section.

```php
'Larinfo' => Matriphe\Larinfo\LarinfoFacade::class,
```

## Usage

To get all info, use `getInfo()` method. It will return this array example.

```php
[
   'host'=> [
       'city'=> '104.20.8.94',
       'country'=> 'US',
       'hostname'=> '',
       'ip'=> '104.20.8.94',
       'loc'=> '37.7697,-122.3933',
       'org'=> 'AS13335 Cloudflare, Inc.',
       'phone'=> '',
       'postal'=> '94107',
       'region'=> ''
   ],
   'client'=> [
       'city'=> 'Bekasi',
       'country'=> 'ID',
       'hostname'=> '',
       'ip'=> '180.252.202.108',
       'loc'=> '-6.2349,106.9896',
       'org'=> 'AS17974 PT Telekomunikasi Indonesia',
       'phone'=> '',
       'postal'=> '',
       'region'=> ''
   ],
   'server'=> [
       'software'=> [
           'os'=> 'Darwin (macOS 10.12.6 )',
           'distro'=> '',
           'kernel'=> '16.7.0',
           'arc'=> 'x86_64',
           'webserver'=> 'nginx/1.12.0',
           'php'=> '7.0.20'
       ],
       'hardware'=> [
           'cpu'=> 'Intel® Core™ i5-3210M CPU @ 2.50GHz',
           'cpu_count'=> 4,
           'model'=> 'MacBook Pro',
           'virtualization'=> '',
           'ram'=> [
               'total'=> 8589934592,
               'free'=> 8578883584
           ],
           'swap'=> [
               'total'=> 4294967296,
               'free'=> 747110400
           ],
           'disk'=> [
               'total'=> 754593608704,
               'free'=> 265534066688
           ]
       ],
       'uptime'=> [
           'uptime'=> '4 days, 8 hours, 38 seconds',
           'booted_at'=> '2017-07-28 07:12:21'
       ]
   ],
   'database'=> [
       'driver'=> 'MySQL',
       'version'=> '5.7.18'
   ]
]
```

Other method you can use are:

 * `getHostIpinfo` to get host IP info
 * `getClientIpinfo` to get client IP info
 * `getServerInfoSoftware` to get server software info
 * `getServerInfoHardware` to get server hardware info
 * `getUptime` to get server uptime
 * `getServerInfo` to get server info
 * `getDatabaseInfo` to get database info
 
### Config

IP information is taken using [ipinfo.io](http://ipinfo.io/) service. If you've registered and has token access, put your token in the `config/services.php` in `ipinfo` variable.

```php
'ipinfo' => [
	'token'  => 'your_ipinfo_token',
],
```

If you don't want to hit ipinfo.io rate limit, you can cache it using Laravel built-in cache.

## License

The GPLv3 License. Please see [License File](LICENSE.md) for more information.