
## mimic導入

基本的に以下のリンクを参照
https://mimic.physionet.org/tutorials/install-mimic-locally-windows/

### windowsに導入したPostgreSQLをsql shell (psql)から使う
アプリ検索からpsqlなどで検索して起動。<br>
Serverなど聞かれるがひとまずデフォルト設定で入ればいいのでパスワード以外Enterでスキップ。<br>
以下の操作の設定部分はpsql起動ごとに必要。コマンドなどは目的に応じて。<br>

作成したmimicデータベースに接続。
`\c mimic;`
作成したスキーマを設定
`set search_path to mimiciii;`
.sqlファイルなどを実行。
`\i D:/mimic_iii/mimic-code/buildmimic/postgres/postgres_create_tables.sql`
`\i D:/mimic_iii/mimic-code/concepts/severityscores/sapsii.sql`

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

