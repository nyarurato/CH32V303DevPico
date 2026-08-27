# CH32V303DevBoardPico

Raspberry Pi Pico と同じ外形・ピンヘッダ位置を保ちながら、**WCH CH32V303CBT6**（RISC-V / 144MHz / LQFP-48）を搭載した開発ボードです。
現状：裏返しスタッキングにより既存の Pico 互換拡張基板（CAN 拡張 + 24V 電源監視）にそのまま搭載可。

設計には **嘉立创EDA（EasyEDA Pro）** を使用しています。

## 概要

| 項目 | 内容 |
|---|---|
| MCU | CH32V303CBT6（LQFP-48 / RISC-V / 144MHz） |
| 基板サイズ | 21.0 × 51.3 mm（Raspberry Pi Pico 互換外形） |
| レイヤー | 2層 |
| 電源 | USB Type-C 5V 入力 → 3.3V LDO |
| クロック | HSE 16MHz クリスタル |
| デバッグ | SWD（H1: SWDIO / GND / SWCLK の3ピン） |

## 構成 V0.1

![](output/v0_1/Schematic.png)
![](output/v0_1/3D_PCB.png)

## 製造データ（`output/v0_1/`）

| ファイル | 内容 |
|---|---|
| `Gerber.zip` | Gerber / ドリルデータ |
| `BOM.xlsx` | 部品表 |
| `PickAndPlace.xlsx` | SMT 実装座標 |
| `Schematic.pdf` / `.svg` / `.png` | 回路図 |
| `3D_PCB.png` | PCB 3D レンダリング |

発注先：JLCPCB（ Gerber.zip + BOM/PickAndPlace は JLCPCB SMT の形式に対応）

## 既知の制限・注意事項

| # | 項目 | 重要度 | 対応 |
|---|---|---|---|
| 1 | 裏返しスタッキング時の物理干渉（部品高さ） | 高 | 実装前に実物確認、必要なら延長ヘッダ |
| 2 | 3V3_EN（拡張 pin37→H2-17）無接続 | 中 | 拡張基板側プルアップ有無を確認 |
| 3 | LSE 有効化時に X2 未実装のためハング | 低 | RTC 不使用またはタイムアウト処理 |
| 4 | シリアルブート不可（BOOT0=GND 固定） | 低 | SWD 書き込みで代替 |
| 5 | USB ESD 保護なし | 低 | 屋外使用・量産時は対策推奨 |


## ライセンス

[CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)