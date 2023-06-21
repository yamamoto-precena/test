# 環境構築手順
## 前提
教材作成ツールの改修は「Windows環境」で実施することを前提とするため、こちらには「Windows環境構築手順」を記載する。

## 手順
### １．sourcetreeをインストールする

公式サイトからダウンロードし、インストールする。
<https://www.sourcetreeapp.com/>


・registration：スキップ

・Pick tools to download and install：gitのみインストール

・preferences

　　コミットした時に使用するユーザ名とメールアドレスを入力
  
　　ユーザー名例：yamamoto-precena
   
・SSHキー読み込み：いいえ

　　後ほど設定する

### ２．SSHキーの設定

（１）ツール→SSHキーの作成/インポートを選択

（２）Putty Key Generator画面にて「Generate」を選ぶ

（３）プログレスバー下の何もない場所をマウスでぐりぐり動かして乱数を生成

（４）Key PassphraseとConfirm Passphraseに自分で決めたパスワードを入力

（５）「Save Public Key」ボタンを押し、公開鍵ファイル名：id_rsa_Github_[YourName].pubにて適当なディレクトリに保存

（６）「Save Private Key」でボタンを押し、秘密鍵ファイル名：id_rsa_Github_[YourName].ppkにて適当なディレクトリに保存

（７）Key欄：Public key for pasting into OpenSSH authorized keys file 下のテキストボックス文字列を、OpenSSH公開鍵ファイル名：id_rsa_Github_[YourName]_OpenSSH.txtにて適当なディレクトリに保存

（８）Github上で公開鍵を登録する。

　　①以下URLにアクセスし、「New SSH Key」を選択
  
　　<https://github.com/settings/keys>
  
  　　②適当なタイトルをつけて、Keyのところに（７）OpenSSH公開鍵のテキストの内容をコピーして「Add SSH Key」で登録する
   
（９）Putty Key Generator画面にて「Load」ボタンを押し（６）で保存した秘密鍵ファイルを指定する。

（１０）ツール→オプションからオプション画面を開き、認証タブに移動する

（１１）「追加」を押し、「ホスティングアカウントを設定」画面にて以下の通り設定する。
```
　　ホスティングサービス：GitHub
  　優先するプロトコル：SSH
  　認証：OAuth
  　ユーザー名：GitHubのユーザー名（例：yamamoto-precena）
    OAuthトークンを再読み込みを押下してOK
 ```   
（１２）コマンドプロンプトにて以下コマンドを実行する。（一度、接続を通し信頼させなければエラーが発生してしまうため）

　　``` %LOCALAPPDATA%\SourceTree\app-3.4.13\tools\putty\plink.exe  git@github.com ```
  ※app-3.x.xxを必要に応じて書き換え

  本当に接続してよいかを聞かれるため「y」を入力してエンターを押す。
  　
  
参考：

<https://qiita.com/neon-izm/items/55de775dd50024403c5d>

<https://qiita.com/jjk/items/2d21c663eb195f3db5df>

### ３．material_making_toolリポジトリをクローンする

クローンタブを開き、URLに
``` git@github.com:precena-dev/material_making_tool.git ```\
を指定してクローンを実行する。
