
## mimic導入

基本的に以下のリンクを参照
https://mimic.physionet.org/tutorials/install-mimic-locally-windows/



### wslでの操作（回り道）
結局Pythonがwindowsにあるので、windows側での構築が必要だった。
wslにPostgreSQLを導入する（以下リンク）
https://docs.microsoft.com/ja-jp/windows/wsl/tutorials/wsl-database

linuxサーバーとwslの挙動が異なるため、認証をいじっても
以下のコマンドでpostgreSQLをハンドリングする際のデフォルトユーザーpostgresへのログインが必要
`su postgres`
もしかして以下でも行ける？
`sudo make ~`

wsl上で以下のリンクを参照したコマンドを実行
https://mmbiostats.com/mimic_how_to

これで構築したDBにログインユーザーで観閲しに行くためにはpostgresへのログインののち、
`psql`
で入ったあと、ログインユーザーと同じ名前のroleを作成する。
`CREATE ROLE KEYTSUDA WITH SUPERUSER LOGIN PASSWORD $PATHWD`

必要に応じて権限を減らす。以下のリンクを参照。
https://www.dbonline.jp/postgresql/role/index2.html

これでログインユーザーのターミナルから直接DBへのアクセスができるようになった。


