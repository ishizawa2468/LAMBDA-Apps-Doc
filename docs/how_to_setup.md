# LAMDBA-Apps 処理フロー/成果物ドキュメント

## 1. 概要
本ドキュメントは、図中に示された LAMDBA-Apps（図中表記）の構成要素と処理フローを文章化したものです。ファイル名・処理名は図中表記を踏襲し、必要に応じて補足説明を付記します。

## 2. 構成要素（図中表記）

### 2.1 入力・参照データ
- 1次実験データ
- 露光データ.spe
- 時系列XRDデータ.nxs
- 校正参照用ランプデータ.csv
- 校正用ODフィルターデータ.spe
- XRD校正データ.poni

### 2.2 アプリ名（図中表記）
- AppManager（起動）
- RadiationSpectraRotator
- PlanckThermoEmulator
- XRDSpotAnalyzer
- HDFViewer
- LAMBDA-Melting

### 2.3 処理・出力データ（図中表記）
- 露光データ_回転中心_回転角度.spe
- 校正されたスペクトルデータ.hdf
- 温度分布・誤差データ.hdf（by Planck fitting）
- 温度、誤差データ（by 二色法）
  - ※file出力未対応、図の出力あり
- cake・patternなどXRD処理データ.hdf
- 温度データ処理
- XRDデータ処理
- 1 runにおける温度・XRD・圧力など処理済みデータ.hdf
- 処理されたデータ

### 2.4 解析主体
- 解析する人
- 何かの解析処理プログラム
  - 図中の説明にある通り、必要なデータにはそれぞれのアプリ内にあるクラスでアクセスでき、notebook などで解析する前提。

### 2.5 図の凡例（図中表記）
- 判例
- アプリ名
- ライブラリロゴ

## 3. 処理フロー（図中表記を踏襲）

1. **AppManager（起動）**
   - 各アプリの起動を担う入口。

2. **露光スペクトル系の処理**
   - 入力: 露光データ.spe
   - 参照: 校正参照用ランプデータ.csv、校正用ODフィルターデータ.spe
   - アプリ: RadiationSpectraRotator
   - 出力:
     - 露光データ_回転中心_回転角度.spe
     - 校正されたスペクトルデータ.hdf

3. **温度データ処理**
   - アプリ: PlanckThermoEmulator
   - 入力: 校正されたスペクトルデータ.hdf（および上流のスペクトル処理結果）
   - 出力:
     - 温度分布・誤差データ.hdf（by Planck fitting）
     - 温度、誤差データ（by 二色法）
       - ※file出力未対応、図の出力あり

4. **XRDデータ処理**
   - 入力: 時系列XRDデータ.nxs
   - 参照: XRD校正データ.poni
   - アプリ: XRDSpotAnalyzer
   - 出力: cake・patternなどXRD処理データ.hdf

5. **統合処理（LAMBDA-Melting）**
   - 温度データ処理・XRDデータ処理を統合し、
     1 runにおける温度・XRD・圧力など処理済みデータ.hdf を生成。

6. **HDFViewer での確認**
   - ※ 出力された .hdf ファイルの中身を確認できる。

7. **解析フェーズ**
   - 解析する人 / 何かの解析処理プログラムが、
     処理されたデータをアプリ内クラス経由で参照し、notebook などで解析する。

## 4. 成果物一覧
- 露光データ_回転中心_回転角度.spe
- 校正されたスペクトルデータ.hdf
- 温度分布・誤差データ.hdf（by Planck fitting）
- 温度、誤差データ（by 二色法）
  - ※file出力未対応、図の出力あり
- cake・patternなどXRD処理データ.hdf
- 1 runにおける温度・XRD・圧力など処理済みデータ.hdf

## 5. 前提/依存
- AppManager により各アプリを起動できること。
- RadiationSpectraRotator / PlanckThermoEmulator / XRDSpotAnalyzer / LAMBDA-Melting / HDFViewer が利用可能であること。
- 入力ファイル（露光データ.spe、時系列XRDデータ.nxs など）が揃っていること。
- 出力された .hdf は HDFViewer で内容確認が可能であること。
- 解析はアプリ内クラスでデータにアクセスし、notebook などで実施する前提であること。
