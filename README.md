#gnn-counterattack-xai-v2

#概要

このリポジトリは卒論で取り組んでいる研究のもので、グラフニューラルネットワーク（GNN）に経験的・物理的な制約を加えたモデルを用いて「カウンターアタックの成功予測」を行い、その後アテンション係数の可視化や順列特徴重要度、ＧＮＮExplainerなどの事後解析手法なども組み合わせて、深層学習で課題となっている「ブラックボックス性」にアプローチし、モデル・結果の「説明可能性（解釈性）」を向上させようという研究である。
GNNによるカウンターアタック成功予測の先行研究のデータによる実行とScientificDataによって公開されているデータに独自の前処理を施したデータを用いた実行を行っている。
論文本文：https://drive.google.com/drive/folders/1j4fvuqVRgeO9BCnPBBGGnCsC7ZTIvmsn?usp=sharing

#研究内容の説明

※詳しい内容の説明は以下の参考資料を見て頂ければと思います。
[論文説明資料（PDF）を表示する](./論文説明資料_磯田龍哉.pdf)
<img width="1619" height="771" alt="スクリーンショット 2026-05-07 17 19 09" src="https://github.com/user-attachments/assets/e1aa412f-386c-43c8-876f-3269e74b503d" />


以下では上記説明資料を抜粋して研究内容の概要を説明する。


#研究動機

<img width="1750" height="989" alt="スクリーンショット 2026-05-07 17 25 10" src="https://github.com/user-attachments/assets/b5013e5d-423c-4d32-a846-0be899e97280" />





#グラフニューラルネットワーク（GNN）とは

<img width="1637" height="921" alt="スクリーンショット 2026-05-07 17 26 31" src="https://github.com/user-attachments/assets/0affb39b-21dc-4732-98ce-5011fe8244fc" />






#本研究の目的

<img width="1619" height="749" alt="スクリーンショット 2026-05-07 17 39 21" src="https://github.com/user-attachments/assets/d8b45c6b-4d18-44b9-afc1-9789104d96a5" />



#提案手法

提案手法は２つ（アテンション係数の可視化を行うためどちらもGATをベースに拡張する方式を取っています）

-提案手法１：経験的な制約を加えたモデル

具体的には、『将来位置が近くなる選手同士にアテンションを振り』、攻撃選手の集団推進力損失を実装しました。
<img width="1782" height="995" alt="スクリーンショット 2026-05-07 17 28 17" src="https://github.com/user-attachments/assets/f8169311-2174-41bd-b5d8-687c63965cc1" />



-提案手法２：物理的制約を加えたモデル

具体的には、等速直線運動を仮定し、『将来予測位置が実際の位置と逸脱している選手をノイズとして除去する』アーキテクチャを実装しました。




#結果
順列特徴重要度（予測全体において重要であった特徴量の重要度）

<img width="1801" height="983" alt="スクリーンショット 2026-05-07 17 29 11" src="https://github.com/user-attachments/assets/66d69d6c-962d-4f34-8e66-a2a17d2755d8" />

GNN Explainer（そのシーンにおいて不可欠だった選手の関係性や特徴量）

下の例であれば、カウンターの成功シーンにおいて黄色いエッジの選手同士の関係性が不可欠であったということがわかる。
<img width="1665" height="905" alt="スクリーンショット 2026-05-07 17 30 27" src="https://github.com/user-attachments/assets/c026bedb-8e70-41c8-be8c-da9b470f03df" />

右側の順列特徴重要度は予測全体における特徴の重要度であり、左側は成功シーンにおける重要であった特徴量である。これらを比較すると全体法則としてはx速度とゴールへの距離がカウンター攻撃には重要であることがわかるが、この成功シーンにおいてはx速度とゴールへの距離よりx座標の重要度が高い。
→シーンによって情報の優先順位を変更していることが読み取れる

<img width="1681" height="913" alt="スクリーンショット 2026-05-07 17 30 49" src="https://github.com/user-attachments/assets/a2335e08-3793-44b2-b710-581a8dafccca" />




#結論

<img width="1729" height="897" alt="スクリーンショット 2026-05-07 17 36 33" src="https://github.com/user-attachments/assets/dbf12fd8-7bff-47b5-b142-76a3d1a35e41" />


#ファイルの説明

-論文データによる実行
提案手法１：GNN_CounterAttack_Thesis_show_PIGNN_v4.ipynb

提案手法２：GNN_CounterAttack_Thesis_show_PIGNN_v7.ipynb


-公開データによる実行

前処理：scientificdata_one6.ipynb

提案手法１：GAT_CounterAttack_Prediction_Train_Scientific8_V6_take3.ipynb

提案手法２：GAT_CounterAttack_Prediction_Train_Scientific9.ipynb
