#gnn-counterattack-xai-v2

#概要

このリポジトリは卒論で取り組んでいる研究のもので、グラフニューラルネットワーク（GNN）に経験的・物理的な制約を加えたモデルを用いて「カウンターアタックの成功予測」を行い、その後アテンション係数の可視化や順列特徴重要度、ＧＮＮExplainerなどの事後解析手法なども組み合わせて、深層学習で課題となっている「ブラックボックス性」にアプローチし、モデル・結果の「説明可能性（解釈性）」を向上させようという研究である。
GNNによるカウンターアタック成功予測の先行研究のデータによる実行とScientificDataによって公開されているデータに独自の前処理を施したデータを用いた実行を行っている。


[論文説明資料（PDF）を表示する](./論文説明資料_磯田龍哉.pdf)
<img width="1619" height="771" alt="スクリーンショット 2026-05-07 17 19 09" src="https://github.com/user-attachments/assets/e1aa412f-386c-43c8-876f-3269e74b503d" />




#提案手法

提案手法は２つ（アテンション係数の可視化を行うためどちらもGATをベースに拡張する方式を取っています）

-提案手法１：経験的な制約を加えたモデル
具体的には、『将来位置が近くなる選手同士にアテンションを振り』、攻撃選手の集団推進力損失を実装しました。

-提案手法２：物理的制約を加えたモデル
具体的には、等速直線運動を仮定し、『将来予測位置が実際の位置と逸脱している選手をノイズとして除去する』アーキテクチャを実装しました。



#ファイルの説明

-論文データによる実行
提案手法１：GNN_CounterAttack_Thesis_show_PIGNN_v4.ipynb

提案手法２：GNN_CounterAttack_Thesis_show_PIGNN_v7.ipynb


-公開データによる実行

前処理：scientificdata_one6.ipynb

提案手法１：GAT_CounterAttack_Prediction_Train_Scientific8_V6_take3.ipynb

提案手法２：GAT_CounterAttack_Prediction_Train_Scientific9.ipynb
