# windows setup 201015

## 本体設定
* コトネットワークデバイス登録
* windows update
* microsoft store アプリアップデート
* oneドライブ自動起動停止
* マウス
    - ポインターの精度を高めるオフ
    - 1600dpi
* 共有
    - 名前変更 kawahara-windows-201002
* ディスプレイ
    - 夜間モード 19:30~6:00
* エクスプローラー表示設定: 隠しファイル、ファイル名拡張子

## ソフトウェアインストール
* chrome
    - ログイン
    - New Tab Redirect
    - `chome://frags`Tab Groups, TabGroupsCollapse
* bitwarden
* dropbox
* google日本語入力: スペースの入力半角
* nvidia control panel
* geforce experience
    - ドライバアップデート
* unityhub
    - unity 2020.1.9f1, 2019.4.11f1
    - androidbuild, doc, 日本語
* vscode: サインインgithub
* visual studio
* docker desktop
* thunderbird
    - KAWAHARA Mizuki
    - kotojpn.sakura.ne.jp, STARTTLS
    ```html
    河原 水月<br>
    <a href="tel:080-6130-3667">080-6130-3667</a><br>
    <a href="mailto:k_mizuki@koto.co.jp">k_mizuki@koto.co.jp</a>
    ```
* slack
* skype
* office
* windows terminal
* ubuntu 20.04
* フォント: HackGen35NerdConsole-Regular
* 7-zip
* Adobe Acrobat Reader: 連続見開き、解像度システム設定

## 開発環境構築

### WSL2セットアップ
管理者としてPowerShellを開き、以下を実行
linux用windowsサブシステムを有効にする
```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
仮想マシンの機能を有効にする
```PowerShell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
最新の<a href="https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi">x64 マシン用 WSL2 Linux カーネル更新プログラム パッケージ</a>をダウンロード

WSL2を既定に設定
```PowerShell
wsl --set-default-version 2
```
ユーザセッティングの追加
```PowerShell
code -n "$env:USERPROFILE\.wslconfig"
```
```.wslconfig
[wsl2]
swap=0
```

### windows terminal
settingを開き、defaultprofileをubuntuに変更
```json
"defaultProfile": "{07b52e3e-de2c-5db4-bd2d-ba144ed6c273}"
"theme": "dark"
"fontFace": "HackGen35NerdConsole-Regular"
"fontSize": 12
```

zsh導入
```bash
$ sudo apt install zsh
```
パスをコピーし`chsh`で貼り付け
```bash
$ chsh -s $(which zsh)
```

git初期値設定:名前・アドレス・キーチェイン・エディタ
```zsh
$ git config —-global user.name “k_mizuki”
$ git config --global user.email k_mizuki@koto.co.jp
$ git config --global core.editor vim
$ git config --global credential.helper store
```
ドットファイルクローン
```zsh
$ git clone (dotfiles)
```
.zshrcをバックアップ
```zsh
$ mkdir backup
$ mv .zshrc backup
```
シンボリックリンク貼る
```zsh
$ ln -s dotfiles/ubuntu/.zshrc ~
```
新しいタブで再度読み込み（sourceはしないこと）command+t
rubyインストール
```zsh
$ brew install rbenv
$ rbenv install -l
$ rbenv install 2.7.2
$ rbenv global 2.7.2
```
pythonインストール
```zsh
$ brew install pyenv
$ pyenv install -l
$ pyenv install 3.8.5
$ pyenv global 3.8.5
```
pyライブラリ一括インストール
```zsh
$ pip install -r dotfiles/requirements.txt
```
