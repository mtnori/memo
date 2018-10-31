# through-proxy
Proxy環境下での各種設定方法  

### Gradlew  
1. JREのlib/security/cacertsを任意の場所にコピーして使う(直接使っても良いのかも)  
1. プロキシサーバの自己証明書をcacertsストアに追加する  
cacertsファイルのある場所に移動後、以下を実行  
`keytool -import -file [証明書ファイル名] -trustcacerts -alias [適当な名前] -keystore cacerts -storepass changeit`
1. gradlew.batの先頭に以下のように書く  
    1. Windows  
`set JAVA_OPTS=-DproxyHost=[host] -DproxyPort=[port] -Dhttp.proxyUser=[username] -Dhttp.proxyPassword=[password] -Dhttps.proxyUser=[username] -Dhttps.proxyPassword=[password] -Dhttp.nonProxyHosts=[non proxy hosts] -Djavax.net.ssl.trustStore=[証明書ストアのフルパス] -Djavax.net.ssl.trustStorePassword=[証明書ストアのパスワード(デフォルトはchangeit)]`
    1. Linux  
`export JAVA_OPTS="-DproxyHost=[host] -DproxyPort=[port] -Dhttp.proxyUser=[username] -Dhttp.proxyPassword=[password] -Dhttps.proxyUser=[username] -Dhttps.proxyPassword=[password] -Dhttp.nonProxyHosts=[non proxy hosts] -Djavax.net.ssl.trustStore=[証明書ストアのフルパス] -Djavax.net.ssl.trustStorePassword=[証明書ストアのパスワード(デフォルトはchangeit)]"`
1. gralew.batまたは、gradlewの`set DEFAULT_JVM_OPTS=`の行を以下のように編集する  
Java 8 Update 111 からBASIC認証が禁止されたのでこの対応が必要らしい  
`set DEFAULT_JVM_OPTS="-Djdk.http.auth.tunneling.disabledSchemes=\"\""`
1. gradlewコマンドを実行して、gradleがダウンロードされるか確認する
