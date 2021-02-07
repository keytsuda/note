
# mimic experiment note

## building enviroment

基本的に以下のリンクを参照
https://mimic.physionet.org/tutorials/install-mimic-locally-windows/

### windowsに導入したPostgreSQLをsql shell (psql)から使う
2021/01/17<br>
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

## data preproc 

### gru_ode_bayse data preproc
2021/01/17<br>
gru_ode_bayseのリポジトリのreadmeを参考にAdmissions.ipynbから実行。
90歳以上が登録時に300歳になるMIMICの仕様により、
pandasで日付の差分を計算する際に、オーバーフローする(ns計算のため)。
基本的に100年ほど加算された西暦が日付として入っているため、
1950年より前に生まれていると記載されているものを90歳以上として除いた。他は著者のものを採用した。
 
"sapii.csv"がなかったため、DataMerging.ipynbが途中で止まった。
どうやら公式から出ているsqlで計算できる数値の模様。


## mimic-code concepts 
定義や意味に基づいて、データ加工が行われる。
以下の記述に従って、wslを用いたwindowsの方法を実行。
https://github.com/MIT-LCP/mimic-code/tree/master/concepts

一通りのconceptなどは上の.batファイルでPostgreSQL内に作成された。
が、スキーマを設定せずに実行されているので、上のスキーマ（mimiciii）を設定した時とは別のものが作成されている。

ひとまず利用するsapsii scoreはICU-stay一日目のデータを用いて算出されている。つまり滞在1日目終了時点でのスコアが出てくる。
途中経過として、一日終了後のsapsiiスコアを可視化するのがよいか？



