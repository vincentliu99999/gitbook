# URL function

## [http\_build\_query](https://www.php.net/manual/en/function.http-build-query.php)

參數 query data 可為 array 或 object，object 僅有 public 的屬性會被處理

## [parse\_url](https://www.php.net/manual/en/function.parse-url.php)

解析 URL

```php
<?php

$url = 'http://username:password@hostname:9090/path?arg1=value1&arg2=value2#anchor';

var_dump(parse_url($url));
var_dump(parse_url($url, PHP_URL_SCHEME));
var_dump(parse_url($url, PHP_URL_USER));
var_dump(parse_url($url, PHP_URL_PASS));
var_dump(parse_url($url, PHP_URL_HOST));
var_dump(parse_url($url, PHP_URL_PORT));
var_dump(parse_url($url, PHP_URL_PATH));
var_dump(parse_url($url, PHP_URL_QUERY));
var_dump(parse_url($url, PHP_URL_FRAGMENT));

$url_query = parse_url($url, PHP_URL_QUERY);
$query = '';

parse_str($url_query, $query);
var_dump($query);
?>
```

