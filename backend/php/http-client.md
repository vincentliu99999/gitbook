# HTTP Client

## GuzzleHttp

* [doc - eng](http://docs.guzzlephp.org/en/stable/)
* [doc - zh\_cn](https://guzzle-cn.readthedocs.io/zh_CN/latest/)

php.ini 必須啟用 `allow_url_fopen`

```bash
composer require guzzlehttp/guzzle:~6.0
```

1. 建立 client, base uri follow [RFC 3986, section 2](http://tools.ietf.org/html/rfc3986#section-5.2)
2. 發送 request

