# Shell

* [Z Shell\(Zsh](https://www.zsh.org/)[\)](https://github.com/ohmyzsh/ohmyzsh)
* [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) 管理 zsh 設定
  * 需求: zsh, curl, wget, git
  * zsh-completions 打字按右鍵，可自動完成
  * zsh-syntax-highlighting

## Oh My Zsh

* [zsh-completions](https://github.com/zsh-users/zsh-completions)
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

```text
# 設定預設 shell, 之後登出並重新登入
chsh -s /usr/local/bin/zsh
chsh -s $(which zsh)

echo $0
which zsh
```

### [Powerlevel9k](https://github.com/Powerlevel9k/powerlevel9k)

```bash
# 安裝 Powerlevel9k
brew tap sambadevi/powerlevel9k
brew install powerlevel9k

# mac 安裝字型 https://github.com/powerline/fonts
# nerd-fonts https://github.com/ryanoasis/nerd-fonts#option-4-homebrew-fonts
# POWERLEVEL9K_MODE='nerdfont-complete'
brew cask install font-sourcecodepro-nerd-font
brew cask install font-firacode-nerd-font

# 修改後
vi ~/.zshrc
exec $SHELL
```

`POWERLEVEL9K_LEFT_PROMPT_ELEMENTS`

`POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS`

VS Code 字型設定

```javascript
{
  "terminal.integrated.fontFamily": "Hack Nerd Font",
  "terminal.integrated.fontSize": 18
}
```

## Reference

[UNIX shell differences and how to change your shell \(Monthly Posting\)](http://www.faqs.org/faqs/unix-faq/shell/shell-differences/)

