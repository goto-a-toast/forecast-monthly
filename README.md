# 月次時系列予測 - 機械学習モデル比較

## 概要

このプロジェクトは、月次の時系列データに対して複数の機械学習モデルを適用し、予測精度を比較するためのJupyter Notebookです。売上予測、需要予測、在庫計画など、月次集計データの分析に活用できます。

## Google Colabで実行

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/goto-a-toast/forecast-monthly/blob/main/timeseries_prediction_monthly.ipynb)

上記のバッジをクリックすると、Google Colabでnotebookを直接開くことができます。

## 機能

### 対応モデル

本notebookでは、以下の8つの機械学習モデルを比較します：

1. **線形回帰（Linear Regression）** - シンプルな線形モデル
2. **Ridge回帰** - L2正則化による過学習の抑制
3. **Lasso回帰** - L1正則化による特徴選択
4. **Random Forest** - アンサンブル学習による非線形予測
5. **Gradient Boosting** - 勾配ブースティング
6. **XGBoost** - 高性能な勾配ブースティング
7. **LightGBM** - 高速・高精度な勾配ブースティング
8. **Prophet** - 時系列専用モデル（Facebookが開発）

### 主な特徴

- **月次データに最適化**：年次・四半期の季節性を考慮
- **自動特徴量生成**：年、月、四半期、周期性（sin/cos変換）などの時間特徴を自動生成
- **モデル比較**：MAPE、RMSE、MAE、R²スコアで精度を多角的に評価
- **可視化機能**：予測結果と実績値の比較グラフ、誤差分析、特徴量重要度の表示
- **将来予測**：学習済みモデルで未来の値を予測し、CSV出力

## 使い方

### 1. データの準備

CSVファイルを準備します。以下のフォーマットが必要です：

- **日付列**：YYYY-MM-DD または YYYY-MM 形式
- **目的変数列**：予測したい数値データ
- （オプション）その他の特徴量列

例：
```
date,MP
2020-01-01,1500000
2020-02-01,1650000
2020-03-01,1800000
...
```

### 2. 設定のカスタマイズ

notebookの「2. Configuration」セクションで以下を設定：

```python
DATE_COLUMN = 'date'           # 日付列の名前
TARGET_COLUMN = 'MP'           # 予測対象の列名
TEST_MONTHS = 6                # テスト期間（月数）
TARGET_DISPLAY_NAME = 'Target' # グラフ表示用の名前
TARGET_SCALE = 1_000_000       # 表示用のスケール（100万など）
TARGET_UNIT = 'Million'        # 単位の表示名
```

### 3. 実行

Notebookのセルを順番に実行します：

1. ライブラリのインストール・インポート
2. 設定
3. データアップロード
4. データ前処理
5. 特徴量エンジニアリング
6. 訓練/テスト分割
7. モデル学習・評価
8. 結果の比較・可視化
9. 将来予測
10. 結果のエクスポート

## 適用可能なユースケース

- 月次売上予測
- 月次需要予測
- 月次在庫計画
- 月次収益予測
- 月次財務指標の予測
- その他の月次集計データ

## 出力結果

### 評価指標

各モデルは以下の指標で評価されます：

- **MAPE（Mean Absolute Percentage Error）**：平均絶対パーセント誤差（低いほど良い）
- **RMSE（Root Mean Squared Error）**：二乗平均平方根誤差
- **MAE（Mean Absolute Error）**：平均絶対誤差
- **R²スコア**：決定係数（高いほど良い、1.0が最大）

### 可視化

- モデル別の精度比較（MAPE、R²）
- 予測値と実績値の比較グラフ
- 月次予測誤差の可視化
- 特徴量の重要度（ツリーベースモデル）
- 将来予測の可視化

### エクスポート

予測結果は `forecast_results_monthly.csv` として自動ダウンロードされます。

## 必要なライブラリ

notebookで自動的にインストールされます：

- pandas
- numpy
- matplotlib
- scikit-learn
- xgboost
- lightgbm
- prophet

## 日次版との違い

本notebookは**月次データ**に特化しています：

- 月次粒度に適応（曜日などの日次特徴は不使用）
- 月次パターンの季節性検出を最適化
- テスト期間を日数ではなく月数で指定
- 四半期・年次パターンを重視

## ライセンス

このプロジェクトは自由に使用・改変できます。

## サポート

問題が発生した場合は、GitHubのIssuesでお知らせください。
