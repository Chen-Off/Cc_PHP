GeoIP 的简便傻瓜使用方式（获取IP所在的地址，国家）
========================================
<p>比较着急，没有全部使用官方所提供的方法，直接挂载在网站目录下。</p>
官方操作方法：
https://github.com/maxmind/geoip-api-php
http://maxmind.github.io/GeoIP2-php/

###下载/运行 composer.phar 安装依赖库
```wget https://getcomposer.org/download/1.2.0/composer.phar```

```php composer.phar require geoip/geoip:~1.16```

```php composer.phar require geoip2/geoip2:~2.0```


###下载IP库   ```http://dev.maxmind.com/zh-hans/geoip/``` 

```http://dev.maxmind.com/zh-hans/geoip/legacy/geolite/``` 中下载一代

```wget http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz```    一代

```gunzip GeoLiteCity.dat.gz```

```http://dev.maxmind.com/geoip/geoip2/geolite2/``` 中下载二代


###使用  一代

```
require 'vendor/autoload.php';

$gi = geoip_open("GeoLiteCity.dat",GEOIP_STANDARD);

echo geoip_country_code_by_addr($gi, "24.24.24.24") . "\t" .
    geoip_country_name_by_addr($gi, "24.24.24.24") . "\n";
echo geoip_country_code_by_addr($gi, "80.24.24.24") . "\t" .
    geoip_country_name_by_addr($gi, "80.24.24.24") . "\n";

geoip_close($gi);
```

###使用二代


