# LAMBDA-Apps

## このリポジトリについて

このドキュメントリポジトリは、

- LAMBDAデータ解析処理の概要
- 複数のリポジトリの連携方法・導入手順・構成図

をまとめたものです。

## プロジェクトの概要

### プロジェクト全体の構成・処理の流れの図

![プロジェクト全体の図](./images/process_flow.drawio.svg)

### 見方

- 紫の実験生データを起点に、矢印がデータの流れを示しています。
- `Streamlit` ロゴがあるアプリケーションはGUI操作が可能です。
- `Jupyter` ロゴは基本的にjupyter notebook形式 (`.ipynb`ファイル) です。

### 各アプリの役割

- [AppManager](https://github.com/ishizawa2468/AppManagerForStreamlit): 起動や終了を担うStreamlitアプリ管理アプリ。
- [HDFViewer](https://github.com/ishizawa2468/HDFViewer): 各アプリで出力された[HDF5](https://ja.wikipedia.org/wiki/Hierarchical_Data_Format)ファイルの中身を閲覧・CSV出力をするアプリ
- [RadiationSpectraRotator](https://github.com/ishizawa2468/RadiationSpectraRotator): 輻射データを回転補正するアプリ。
- [PlanckThermoEmulator](https://github.com/ishizawa2468/PlanckThermoEmulator): 輻射スペクトルから温度を計算するアプリ。
- [XRDSpotAnalyzer](https://github.com/ishizawa2468/XRDSpotAnalyzer): XRD回折線ごとの時系列変化を可視化するアプリ。

## セットアップ手順

[docs/how_to_setup.md](./docs/how_to_setup.md) (TODO)を参照してください。

## 利用シーン
(TODO)
主に２つに大別されます。

1. データを持った1つのPC内でスタンドアローンアプリとして使用する
    - 利点
        - hoge
    - シーン例
        - hoge

2. データを持ったPCで起動し、他のPCからLAN経由でアクセスして使用する
    - 利点
        - hoge
    - シーン例
        - hoge

## デモ
(TODO)
解析の流れの一例です。一時停止などしたい場合は `docs` にある `~.mp4` をダウンロードしてください。
