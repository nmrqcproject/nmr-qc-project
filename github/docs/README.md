# NMR Quantum Computer Project (EFNMRQC)

高専生による地球磁場NMR（核磁気共鳴）方式を用いた量子コンピュータの製作および評価プロセスを記録するリポジトリです。

This repository logs the design, DSP signal processing, and HDL/hardware implementation of an Earth's Field NMR (EFNMR) Quantum Computer project.

---

## 概要 (Overview)

- **目的**: 地球磁場を利用したNMR原理による量子ビット操作および信号検出システムの構築
- **開発環境**: Python (DSP/FFT解析), Verilog HDL (FPGAパルス制御), M5Stack, VS Code
- **主要機能**: 
  - FID (Free Induction Decay) 信号のシミュレーションとFFT周波数解析
  - R-2RラダーDACを用いたアナログ波形生成とノイズ対策

---

## システム構成 (System Architecture)

- **コイル**: 偏極・受信兼用コイル（エナメル線 + 透明塩ビ管）
- **信号処理**: 独自設計オペアンプ回路 + アルミシールドケース
- **電源部**: 鉛バッテリー + パワーMOSFET制御（低ノイズ電源化）
- **測定・監視**: M5Stack Lite, ロジックアナライザ, オシロスコープ

---

## 開発ログ (Development Logs)

詳細な実験データや回路設計メモは `docs/` ディレクトリに収録しています。

| 日付 | トピック | 概要 | リンク |
| :--- | :--- | :--- | :--- |
| 2026-06-04 | R-2Rラダー | DAC出力波形の歪み原因調査 | [Log](./docs/2026-06-04.md) |
| 2026-04-26 | Verilog HDL | FSM・NCO・DDSによる波形生成原理 | [Log](./docs/2026-04-26.md) |
| 2026-04-25 | パルス制御・FFT | FID信号生成と高速フーリエ変換解析 | [Log](./docs/2026-04-25.md) |
| 2026-04-24-2 | ノイズ | 信号にノイズを混ぜる | [Log](./docs/2026-04-24-1.md)
| 2026-04-24-1 | 信号作製 | s(t) = A sin(2πft) e^(-t/T2) の実装 | [Log](./docs/2026-04-24-1.md) |