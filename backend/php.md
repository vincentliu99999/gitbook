# PHP

訓練資源

* [\[新人訓練\] PHP 學習](https://issue.104corp.work/trac/ticket/2222)
* [\[PHP 訓練計畫\] 實作Hackathon-Leaderboard](https://issue.104corp.work/trac/ticket/2663)

## 環境設定

```bash
brew install php@7.1
which php
php -v
php -S localhost:8080
```

* PHP executablePath: `/usr/local/opt/php@7.1/bin/php`
* apache module: `/usr/local/opt/php/lib/httpd/modules/libphp7.so`
* PHP config `/usr/local/etc/php/7.1/php.ini`
* PHP-FPM binary `/usr/local/opt/php@7.1/sbin`

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

## [PHP Standards Recommendations\(PSR](https://www.php-fig.org/psr/)\)

[PHP\_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)

[FriendsOfPHP/PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

```bash
composer global require "squizlabs/php_codesniffer=*"
composer global require "friendsofphp/php-cs-fixer"
export PATH=~/.composer/vendor/bin:$PATH

# check version
phpcs --version
phpcbf --version

# config
# ~/.composer/vendor/squizlabs/php_codesniffer/CodeSniffer.conf
phpcs --config-set default_standard PSR2
phpcs --config-show

# check file or folder
phpcs /path/to/code/myfile.php
phpcs /path/to/code

# fix file or folder
php-cs-fixer fix /path/to/code/myfile.php
php-cs-fixer fix /path/to/code
```

## VSCode Extension

* [phpcs](https://marketplace.visualstudio.com/items?itemName=ikappas.phpcs)
* [php cs fixer](https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer) // 可在 settings.josn 指定 coding standard { "phpcs.standard": "PSR2" }

### [PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-intellisense)

只少要有以下其中一個設定，並建議把 php.suggest.basic 設為 false 以避免重複的建議

#### 設定環境變數 PATH

in `~/.zshrc`

```bash
export PATH="/usr/local/opt/php@7.1/bin:$PATH"
```

#### 設定 VSCode executablePath

```javascript
{
  "php.executablePath": "/usr/local/opt/php@7.1/bin/php"
}
```

