# IMG2025

## アプローチ

![image](https://github.com/user-attachments/assets/51615a0d-060b-44b7-bc66-d751a1cbddb1)
[kaggle IMC2024コンペ　上位解法まとめ](https://zenn.dev/yume_neko/articles/050c204c3afd20#%E3%82%B3%E3%83%B3%E3%83%9A%E6%A6%82%E8%A6%81)

### 1. 画像ペア選択　(共通領域を持つ画像ペアの選択）
* 画像から特徴量（Global Feature）を抽出して類似度の高いペアを選択する方法で、ベースラインが採用していたこともあり、上位チームの多くもこちらの戦略を採用していました。
* Global Featureはベースラインが使用していた**DINOv2**を使っているチームが多かった

### 2. 特徴点マッチング　（各画像ペアごとにマッチング点を求める）
特徴点抽出に**ALIKED**、マッチャーに**LightGlue**を組み合わせたSparseマッチングを使用しているチームがほとんど.

* 工夫：画像の回転
ペアごとに画像の片方を0度、90度、180度、270度回転させて、最も一致する回転方向を採用する
![image](https://github.com/user-attachments/assets/293fd841-de90-43c2-a35a-d7460279556a)
[引用：Kaggle Image Matching Challenge 2023を振り返る](https://qiita.com/roniheka/items/ad4717afff1891c0eea3)


### 3. カメラパラメータ推定　（カメラパラメータを推定）
* Structure from Motion (SfM) フレームワークを用いてカメラパラメータを推定
* ベースラインでは**colmap**を使用


## Result
### ver3
2599.9s	21280	Results
2599.9s	21281	Dataset "amy_gardens" -> Registered 196 / 200 images with 3 clusters
2599.9s	21282	Dataset "ETs" -> Registered 22 / 22 images with 1 clusters
2599.9s	21283	
2599.9s	21284	Timings
2599.9s	21285	shortlisting -> total=34.38 sec.
2599.9s	21286	feature_detection -> total=14.15 sec.
2599.9s	21287	feature_matching -> total=1524.59 sec.
2599.9s	21288	RANSAC -> total=76.85 sec.
2599.9s	21289	Reconstruction -> total=896.58 sec.
2600.0s	21290	dataset,scene,image,rotation_matrix,translation_vector
2600.0s	21291	imc2023_haiper,outliers,fountain_image_116.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21292	imc2023_haiper,outliers,fountain_image_108.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21293	imc2023_haiper,outliers,fountain_image_101.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21294	imc2023_haiper,outliers,fountain_image_082.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21295	imc2023_haiper,outliers,fountain_image_071.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21296	imc2023_haiper,outliers,fountain_image_025.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21297	imc2023_haiper,outliers,fountain_image_000.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21298	imc2023_haiper,outliers,fountain_image_007.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
2600.0s	21299	imc2023_haiper,outliers,fountain_image_012.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan

**2600.2s	21300	imc2023_haiper: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21301	imc2023_heritage: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21302	imc2023_theather_imc2024_church: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21303	imc2024_dioscuri_baalshamin: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21304	imc2024_lizard_pond: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21305	pt_brandenburg_british_buckingham: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21306	pt_piazzasanmarco_grandplace: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21307	pt_sacrecoeur_trevi_tajmahal: score=0.00% (mAA=0.00%, clusterness=100.00%)
2600.2s	21308	pt_stpeters_stpauls: score=0.00% (mAA=0.00%, clusterness=100.00%)
2770.5s	21309	amy_gardens: score=30.90% (mAA=18.27%, clusterness=100.00%)
2770.5s	21310	fbk_vineyard: score=0.00% (mAA=0.00%, clusterness=100.00%)
2770.5s	21311	ETs: score=20.52% (mAA=13.46%, clusterness=43.18%)
2770.5s	21312	stairs: score=0.00% (mAA=0.00%, clusterness=100.00%)**


**2770.5s	21313	Average over all datasets: score=3.96% (mAA=2.44%, clusterness=95.63%)
2770.5s	21314	Computed metric in: 170.40 sec.**

### ver6
15297.1s	53644	Results
15297.1s	53645	Dataset "amy_gardens" -> Registered 224 / 200 images with 4 clusters
15297.1s	53646	Dataset "fbk_vineyard" -> Registered 162 / 163 images with 1 clusters
15297.1s	53647	Dataset "ETs" -> Registered 22 / 22 images with 1 clusters
15297.1s	53648	Dataset "stairs" -> Registered 57 / 51 images with 3 clusters
15297.1s	53649	
15297.1s	53650	Timings
15297.1s	53651	shortlisting -> total=51.27 sec.
15297.1s	53652	feature_detection -> total=27.41 sec.
15297.1s	53653	feature_matching -> total=12471.62 sec.
15297.1s	53654	RANSAC -> total=543.02 sec.
15297.1s	53655	Reconstruction -> total=2148.73 sec.
15297.2s	53656	dataset,scene,image,rotation_matrix,translation_vector
15297.2s	53657	imc2023_haiper,outliers,fountain_image_116.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53658	imc2023_haiper,outliers,fountain_image_108.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53659	imc2023_haiper,outliers,fountain_image_101.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53660	imc2023_haiper,outliers,fountain_image_082.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53661	imc2023_haiper,outliers,fountain_image_071.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53662	imc2023_haiper,outliers,fountain_image_025.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53663	imc2023_haiper,outliers,fountain_image_000.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53664	imc2023_haiper,outliers,fountain_image_007.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.2s	53665	imc2023_haiper,outliers,fountain_image_012.png,nan;nan;nan;nan;nan;nan;nan;nan;nan,nan;nan;nan
15297.4s	53666	imc2023_haiper: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53667	imc2023_heritage: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53668	imc2023_theather_imc2024_church: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53669	imc2024_dioscuri_baalshamin: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53670	imc2024_lizard_pond: score=0.00% (mAA=0.00%, clusterness=100.00%)

**15297.4s	53671	pt_brandenburg_british_buckingham: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53672	pt_piazzasanmarco_grandplace: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53673	pt_sacrecoeur_trevi_tajmahal: score=0.00% (mAA=0.00%, clusterness=100.00%)
15297.4s	53674	pt_stpeters_stpauls: score=0.00% (mAA=0.00%, clusterness=100.00%)
15418.9s	53675	amy_gardens: score=28.70% (mAA=16.75%, clusterness=100.00%)
15485.1s	53676	fbk_vineyard: score=30.58% (mAA=28.25%, clusterness=33.33%)
15485.1s	53677	ETs: score=24.71% (mAA=17.31%, clusterness=43.18%)**

**15485.3s	53678	stairs: score=0.00% (mAA=0.00%, clusterness=50.00%)
15485.3s	53679	Average over all datasets: score=6.46% (mAA=4.79%, clusterness=86.66%)**

## エラー
* 列数が違う。１列目のimage_idが存在しない。
* ではなぜbaselineでsubmitができた？


