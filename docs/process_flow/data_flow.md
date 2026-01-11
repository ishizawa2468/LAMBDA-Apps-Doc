# データフロー（入出力の流れ）

```mermaid
flowchart LR
  in_exposure["露光データ.spe"] --> in_exposure_rot["露光データ_回転中心_回転角度.spe"]
  in_exposure_rot --> out_spectrum["校正されたスペクトルデータ.hdf"]
  out_spectrum --> out_planck["温度分布・誤差データ.hdf (by Planck fitting)"]
  out_planck --> out_run["1 runにおける温度・XRD・圧力など処理済みデータ.hdf"]

  in_lamp["校正参照用ランプデータ.csv"] --> in_od_filter["校正用ODフィルターデータ.spe"]
  in_xrd_calib["XRD校正データ.poni"] --> in_xrd_time["時系列XRDデータ.nxs"]

  out_run --> out_run
```

## 注記（source/target が未設定の矢印）

`process_flow.drawio` 内にあるものの、矢印の `source` が未設定で判別できない接続は以下です。

- 不明な接続 → 温度、誤差データ（by 二色法）
- 不明な接続 → 1 runにおける温度・XRD・圧力など処理済みデータ.hdf
- 不明な接続 → cake・patternなどXRD処理データ.hdf

必要に応じてSVGの視認で補完してください。
