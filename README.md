# Windows-Dev-Setup
This is a guideline about dev environment setup in Windows
## Required Software
- VSCode
- Rider
- Pycharm
- Docker Desktop
- pwsh
- Terminal

## Dev environment setup
### chocolatey
[install script](https://chocolatey.org/install#individual)
```ps1
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
### WSL ubuntu installatoon
[link](https://community.chocolatey.org/packages/wsl-ubuntu-2204)
```ps1
choco install wsl-ubuntu-2204
```
### Git installation
```ps1
choco install gitA
```
### Python installation
```ps1
choco install Python3
```
### Dotnet
```
choco install dotnet
```
### oh-my-posh
- Installation
  ```ps1
  choco install oh-my-posh
  ```
- [Config](https://juejin.cn/post/7210596158934433853)
  - Install font
    ```ps1
    choco install font
    ```
  - Install Termnial icon
    ```ps1
    Install-Module -Name Terminal-Icons -Repository PSGallery
    ```
  - Install posh-git
  ```
  Install-Module posh-git -Scope CurrentUser -Force
  ```
  - profile config 
  ```ps1
  code $PROFILE
  oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\mojada.json" | Invoke-Expression

  Import-Module posh-git
  Set-PSReadLineOption -PredictionSource History # 设置预测文本来源为历史记录

  Set-PSReadlineKeyHandler -Key Tab -Function Complete # 设置 Tab 键补全
  Set-PSReadLineKeyHandler -Key "Ctrl+d" -Function MenuComplete # 设置 Ctrl+d 为菜单补全和 Intellisense
  Set-PSReadLineKeyHandler -Key "Ctrl+z" -Function Undo # 设置 Ctrl+z 为撤销

  Set-PSReadLineKeyHandler -Key UpArrow -ScriptBlock {
  [Microsoft.PowerShell.PSConsoleReadLine]::HistorySearchBackward()
  [Microsoft.PowerShell.PSConsoleReadLine]::EndOfLine()
  } # 设置向上键为后向搜索历史记录，并将光标移动到行尾

  Set-PSReadLineKeyHandler -Key DownArrow -ScriptBlock {
  [Microsoft.PowerShell.PSConsoleReadLine]::HistorySearchForward()
  [Microsoft.PowerShell.PSConsoleReadLine]::EndOfLine()
  } # 设置向下键为前向搜索历史纪录，并将光标移动到行尾
  ```

### Github SSH config
[link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```ps1
$email = ""
ssh-keygen -t ed25519 -C $email
cat ~/.ssh/id_ed25519.pub | clip
ssh -T git@github.com
```


