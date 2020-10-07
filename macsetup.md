# mac setup 201002

## 本体設定
* AppleID k_mizuki@koto.co.jp
* ソフトウェアアップデート
* マウス
    - 軌跡の速さ最速
    - スクロールの方向ナチュラル
    - 加速オフ（ターミナル）`$defaults write .GlobalPreferences com.apple.mouse.scaling -1`
* キーボード
    - キーのリピート最速, 時間右から2番
    - 修飾キーControl<->CapsLock
    - ユーザ辞書 チェックボックス全部オフ
* 省エネルギー
    - ディスプレイをオフにするまでの時間 1時間
* 共有
    - 名前変更 kawahara-mac
* ディスプレイ
    - nightshift 19:30~6:00
* Finder
    - デスクトップ全表示
    - 新規Finderウィンドウ-ホームディレクトリ
    - サイドバー ホームディレクトリ
    - 表示オプション 変更日, サイズ, すべてのサイズを計算, 種類オフ->デフォルトとして使用
    - 詳細 すべてのファイル名拡張子表示, 現在のフォルダ内を検索
* ターミナル
    - プロファイルiceberg
    - textボールドテキストにオフ
    - カーソル垂直バー
    - フォントhackgen35nerdconsole-regular, 15pt
* タイムマシン

## ソフトウェアインストール
* xcode
* chrome
    - ログイン
    - New Tab Redirect
    - `chome://frags`Tab Groups, TabGroupsCollapse
* bitwarden
* dropbox
* google日本語入力: スペースの入力半角
* unityhub
    - unity 2020.1.7f1, 2019.4.11f1
    - vsformac, iosbuild, doc, 日本語
* homebrew `$brew doctor`
* vscode: サインインgithub
* dockerdesktop
* thunderbird
    - KAWAHARA Mizuki
    - kotojpn.sakura.ne.jp, STARTTLS
    ```html
    河原 水月<br>
    <a href="tel:080-6130-3667">080-6130-3667</a><br>
    <a href="mailto:k_mizuki@koto.co.jp">k_mizuki@koto.co.jp</a>
    ```
* slack

## 開発環境構築
homebrewは事前に入れておく
```shell
$brew install zsh
$brew install git
$brew install exa
```
git初期値設定:名前・アドレス・キーチェイン・エディタ
```shell
$git config —-global user.name “k_mizuki”
$git config --global user.email k_mizuki@koto.co.jp
$git config —-global credential.helper osxkeychain
$git config --global core.editor vim
```
ドットファイルクローン
```shell
$git clone (dotfiles)
```
.zshrcをバックアップ
```shell
$mkdir backup
$mv .zshrc backup
```
シンボリックリンク貼る
```shell
$ln -s dotfiles/.zshrc ~
```
新しいタブで再度読み込み（sourceはしないこと）command+t
rubyインストール
```shell
$brew install rbenv
$rbenv install -l
$rbenv install 2.7.2
$rbenv global 2.7.2
```
pythonインストール
```shell
$brew install pyenv
$pyenv install -l
$pyenv install 3.8.5
$pyenv global 3.8.5
```
pyライブラリ一括インストール
```shell
$pip install -r dotfiles/requirements.txt
```
