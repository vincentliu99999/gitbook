---
description: coding style guideline
---

# PHP Standards Recommendations - PSR

## [PHP Standards Recommendations\(PSR](https://www.php-fig.org/psr/)\)

* [PHP\_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
* [FriendsOfPHP/PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

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
phpcs --config-set default_standard PSR4
phpcs --config-show

# check file or folder
phpcs /path/to/code/myfile.php
phpcs /path/to/code

# fix file or folder
php-cs-fixer fix /path/to/code/myfile.php
php-cs-fixer fix /path/to/code
```



