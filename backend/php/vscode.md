# VSCode

## Extension

### [PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-intellisense)

至少要有以下其中一個設定，並建議把 php.suggest.basic 設為 false 以避免重複的建議

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

### PSR

* [phpcs](https://marketplace.visualstudio.com/items?itemName=ikappas.phpcs)
* [php cs fixer](https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer) // 可在 settings.josn 指定 coding standard { "phpcs.standard": "PSR2" }

