# NMR Quantum Computer Project (EFNMRQC)

高専生による地球磁場NMR（核磁気共鳴）方式を用いた量子コンピュータの製作および評価プロセスを記録するリポジトリです。

This repository logs the design, DSP signal processing, and HDL/hardware implementation of an Earth's Field NMR (EFNMR) Quantum Computer project.

Xにてリアルタイムで進捗状況を投稿してます。
[リンク](https://x.com/nmrqcproject)
<br>Bloggerでは高校生にもわかるように解説してる記事を投稿してます。
[リンク](https://nmrqcp.blogspot.com/?m=1)

---

## 概要 (Overview)

- **目的**: 地球磁場を利用したNMR原理による量子ビット操作および信号検出システムの構築
- **開発環境**: Python (DSP/FFT解析), Verilog HDL (FPGAパルス制御), M5Stack, VS Code
- **主要機能**: 
  - FID (Free Induction Decay) 信号のシミュレーションとFFT周波数解析
  - R-2RラダーDACを用いたアナログ波形生成とノイズ対策

---

## システム構成 (System Architecture)

- **コイル**: 偏極・受信兼用コイル
  - 呼び径40の透明塩ビパイプをSK11パイプカッターで加工し、2UEWエナメル線（0.5mm）を巻いて自作。
- **信号処理**: 独自設計オペアンプ回路 + アルミシールドケース
  - 微小な信号を捉えるため、超低歪低雑音オペアンプ（AD797BRZ）を採用。環境ノイズ対策としてRS Proのアルミケースに格納。
- **電源部**: 鉛バッテリー + パワーMOSFET制御（低ノイズ電源化）
  - 商用電源からのノイズ混入を防ぐため、12V12Ahの完全密封型鉛蓄電池（WP12-12）を使用し、MOSFET（2SK4017）でスイッチング制御。
- **測定・監視**: M5Stack CoreS3 Lite, 96KHz/24-bit Hi-Fi USBサウンドカード
  - M5Stackとミニリレーユニットでパルスタイミングを制御し、増幅したアナログ信号をサウンドカード経由でPCへ取り込む構成。

---
部品表
---
[部品表はこちら](./github/BOM.md)

---
## プロジェクト解説動画 (Overview Video)

NotebookLMによるEFNMRQCプロジェクトの動画解説と概要です。

<a href="https://youtube.com/shorts/Szdj7OEizAU">
  <img src="https://img.youtube.com/vi/Szdj7OEizAU/0.jpg" width="200" alt="EFNMRQC 解説1">
</a>
<a href="https://youtube.com/shorts/AaI9j7_s0hg">
  <img src="https://img.youtube.com/vi/AaI9j7_s0hg/0.jpg" width="200" alt="EFNMRQC 解説2">
</a>
<a href="https://youtube.com/shorts/5JBLOUBneWA">
  <img src="https://img.youtube.com/vi/5JBLOUBneWA/0.jpg" width="200" alt="EFNMRQC 解説3">
</a>

---

## 開発ログ (Development Logs)

詳細な実験データや回路設計メモは `docs/` ディレクトリに収録しています。

| 日付 | トピック | 概要 | リンク |
| :--- | :--- | :--- | :--- |
| 2026-10-01 | システム統合 | システム統合テスト、痛恨のショートと信号入力の確認 | [Log](./github/2026-10-01.md) |
| 2026-09-27 | シーケンス構築 | M5StackによるMOSFETとリレーの統合制御 | [Log](./github/2026-09-27.md) |
| 2026-09-24 | アンプ完成 | 製作の再開とアナログ受信回路（オペアンプ）の完成・テスト | [Log](./github/2026-09-24.md) |
| 2026-07-04 | コイル制作 | 偏極・受信兼用コイルの製作と通電テストの成功 | [Log](./github/2026-07-04.md) |
| 2026-07-03 | 半田付け | MOSFET駆動回路とオペアンプの実装（半田付け） | [Log](./github/2026-07-03.md) |
| 2026-07-02 | 信号取り込み | USBサウンドカードを用いた信号取り込みとFFT解析テスト | [Log](./github/2026-07-02.md) |
| 2026-07-01 | MOFST制御 | パワーMOSFETによる分極コイルのスイッチング制御テスト | [Log](./github/2026-07-01.md) |
| 2026-06-30 | リレーユニット | M5Stackとミニリレーユニットを使ったコイル制御テスト | [Log](./github/2026-06-30.md) |
| 2026-06-14 | 回路図の訂正 | 回路図の訂正 | [Log](./github/2026-06-14.md) |
| 2026-06-12 | 回路図 | 大まかな回路図の制作 | [Log](./github/2026-06-12.md) |
| 2026-06-04 | R-2Rラダー | DAC出力波形の歪み原因調査 | [Log](./github/2026-06-04.md) |
| 2026-04-26 | Verilog HDL | FSM・NCO・DDSによる波形生成原理 | [Log](./github/2026-04-26.md) |
| 2026-04-25 | パルス制御・FFT | FID信号生成と高速フーリエ変換解析 | [Log](./github/2026-04-25.md) |
| 2026-04-24-2 | ノイズ | 信号にノイズを混ぜる | [Log](./github/2026-04-24-1.md)
| 2026-04-24-1 | 信号作製 | s(t) = A sin(2πft) e^(-t/T2) の実装 | [Log](./github/2026-04-24-1.md) |