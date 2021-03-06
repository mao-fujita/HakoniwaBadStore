# はじめに
箱庭BadStoreは、Kurt Roemer 氏によって開発されたBadStore(http://www.badstore.net 現在はアクセスできない)を、Burp Suiteの拡張として動作するよう書き直したものです。

Burp Suite Japan User Groupの初心者向け[ハンズオンイベント](https://connpass.com/event/56013/)では、BadStoreを題材として利用しました。
オリジナルのBadStoreはisoイメージとして配布されており、実行するには仮想マシンなどからCDブートする必要があります。イベントにおいて、仮想マシンとの通信がうまくできない人が少なからずいたため、より通信トラブルが少なくなることを目的として作成しました。

# ダウンロード
`HakoniwaBadstore.jar`を[ここ](https://github.com/ankokuty/HakoniwaBadStore/releases)からダウンロードしてください。

# 注意
箱庭BadStoreは、デモやセキュリティトレーニング目的のみで利用されることを想定している、脆弱性を意図的に作り込んだセキュアではないプログラムです。
利用によって何らかの損害が生じた場合でも一切責任を負えませんので、自己責任でご利用ください。

# 起動方法
1. 上記リンクからHakoniwaBadStore.jarをダウンロード
2. Burp Suiteを起動し、「Extender」タブを開いてAddボタンをクリック
3. いちばん上の「Select file」ボタンをクリックして、ダウンロードしたHakoniwaBadStore.jarを選択
4. インストール成功すると「BadStore」タブができるのでこれを選択
5. 動かしたいIPアドレスとポート番号を選び「Running」ボタンをクリック
6. もしそのポート番号が使用されている場合は「Address alread in use: bind」とエラーが表示されるので、他のポート番号に変更
7. 任意のブラウザを起動し、指定したIPアドレスとポートにアクセスする(例: http://127.0.0.1:8528)
8. あとはがんばって！

# オリジナルとの相違点
- [DB]
オリジナルではデータベースとしてMySQLが使われていましたが、箱庭BadStoreではSQLiteを使用しています。

- [httpd]
オリジナルではApache HTTP Server が使われていましたが、箱庭BadStoreではEclipse Vert.x を内包してHTTPを処理しています。

- [名前解決]
オリジナルは/etc/hostsファイルを更新するなどによりwww.badstore.netの名前解決をする必要がありましたが、箱庭BadStoreではこの手順を不要にしました。

- [言語]
オリジナルはPerlで書かれていましたが、箱庭BadStoreはBurp Suiteの拡張にするためにJavaで書いています。

- [コマンドインジェクション]
オリジナルにはperlのopen関数利用によるコマンドインジェクションがありましたが、Perl固有の問題であるため箱庭BadStoreでは実装していません。

- [その他]
次の機能は実装していません。
    - SOAP Updates
    - Secret Administration Menu
        - Troubleshooting
        - Supply Chain:  Manage Open Orders
        - Supply Chain:  Check Credit with Supplier

# ライセンス
GNU GPL v2.0 またはそれ以降

# 箱庭BadStoreが利用している外部のライブラリ
- [Burp Extender API](https://github.com/PortSwigger/burp-extender-api) Burp Suite Professional Licence
- [Eclipse Vert.x](http://vertx.io/) Eclipse Public License 1.0 とApache License 2.0 のデュアルライセンス
- [SQLite JDBC Driver](https://github.com/xerial/sqlite-jdbc) Apache License version 2.0
