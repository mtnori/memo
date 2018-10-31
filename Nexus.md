# Sonatype Nexus

## ダウンロード
Nexus Repository OSS(<https://www.sonatype.com/nexus-repository-oss>)をダウンロード。

## インストール
ダウンロードしたファイルを解凍すると、**nexus-3.XX.X-XX**と**sonatype-work**というフォルダが展開される。  
nexus-3.XX.X-XXはアプリケーション本体。sonatype-workはデータ領域。  
なので、sonatype-workを定期的にバックアップすると良い。

## 起動
* Linux  
`nexus-3.XX.X-XX/bin/nexus start`で起動する。
* Windows  
`nexus-3.XX.X-XX/bin/nexus.exe /install Sonatype Nexus Repository Manager`でサービス登録する。

## ブラウザから`http://[ホスト名]:8081/`へアクセスする
初回起動は5分程度かかるので、繋がるまでに時間がかかる。

## ログイン
Welcomeページの右上にある*Sign in*ボタンをクリックし、adminユーザでログインする。  
初期パスワードはadmin123。

## プロキシサーバを経由する場合
ヘッダ部にある歯車アイコンから設定画面に移動し、*SYSTEM→HTTP*から設定。  
プロキシサーバがSSL Dumpを行っている場合、証明書の登録も必要になる。  
それは、*Security→SSL Certificates*から登録可能のはず。
