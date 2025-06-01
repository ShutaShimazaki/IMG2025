# IMG2025

## アプローチ

![image](https://github.com/user-attachments/assets/51615a0d-060b-44b7-bc66-d751a1cbddb1)
[kaggle IMC2024コンペ　上位解法まとめ](https://zenn.dev/yume_neko/articles/050c204c3afd20#%E3%82%B3%E3%83%B3%E3%83%9A%E6%A6%82%E8%A6%81)

### 1. 画像ペア選択　(共通領域を持つ画像ペアの選択）
* 画像から特徴量（Global Feature）を抽出して類似度の高いペアを選択する方法で、ベースラインが採用していたこともあり、上位チームの多くもこちらの戦略を採用していました。
* Global Featureはベースラインが使用していたDINOv2を使っているチームが多かった

### 2. 特徴点マッチング　（各画像ペアごとにマッチング点を求める）
特徴点抽出にALIKED、マッチャーにLightGlueを組み合わせたSparseマッチングを使用しているチームがほとんど.

* 工夫：画像の回転
ペアごとに画像の片方を0度、90度、180度、270度回転させて、最も一致する回転方向を採用する
![image](https://github.com/user-attachments/assets/293fd841-de90-43c2-a35a-d7460279556a)
[引用：Kaggle Image Matching Challenge 2023を振り返る](https://qiita.com/roniheka/items/ad4717afff1891c0eea3)


### 3. カメラパラメータ推定　（カメラパラメータを推定）
* Structure from Motion (SfM) フレームワークを用いてカメラパラメータを推定
* ベースラインではcolmapを使用
* 

