---
description: 套件管理工具
---

# Composer

## [Composer](https://getcomposer.org/) with [Packagist](https://packagist.org/)

```bash
# require PHP 5.3.2+
brew install composer
composer --version

composer init
composer global require <package>
composer require recca0120/laravel-tracy --dev
composer install
composer show # list packages

# 更新 Composer
composer self-update                                         
# Updating to version 1.9.0 (stable channel).
#    Downloading (100%)         
# Use composer self-update --rollback to return to version 1.8.5
```

## Package

### Debug

Tracy

```php
use Tracy\Debugger; // debug only

Debugger::enable(); // debug only

dump($variable);
```

