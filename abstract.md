
# 散発的に計測される時系列データを用いた患者状態の追跡

%タイトルは見直す

## 背景

近年、RWDとも呼ばれる日常診療から得られた医療データの整備が進んできており、疫学的な研究に用いられるだけではなく、患者の転帰予測など、広く日常診療に資する目的に活用されることが期待されている。

活用の一例として、経時的に変化する患者の状態をRWDを用いて観察することがあげられる。RWDには傷病名や処置のみならず、臨床検査値なども経時的に取得されているものもあるため、これを用いた患者間の特徴づけや時間変化の観察を行うことが期待されており、いくつか研究がなされている。
しかし、多くのRWDは時系列方向に散発的に取得され、またその計測時点ごとにすべての変数の値を取得するわけではないため、特定の時間幅でデータを区切ったのみでは、データの取得頻度や取得項目に強く影響され、患者の全身状態の経時変化を正しく追跡することが困難である。

入力の形式が時系列方向に固定されている定型的な時系列モデル（古典的な自己回帰モデルや再帰的ニューラルネットワークなど）を用いてモデリングを行うことは困難であったが、近年の深層学習モデルの発展により、散発的に計測される時系列データを用いた予測を行えるようなモデルがいくつか提案されてきている。そこで我々は、このモデルの潜在変数の経時変化を観察することで、データの粗密の影響を緩和した患者状態のモニタリングが可能であるか、いくつかのモデルに関して追従実験を行った。

## 方法





