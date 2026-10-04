## 部品表 (Bill of Materials)

本プロジェクト（EFNMR量子コンピュータ）を構成する主なハードウェア部品のリストです。

### 1. マイコン・データ収録系
| 部品名 | 型番・仕様 | 数量 | 備考 |
| :--- | :--- | :--- | :--- |
| メインマイコン | [M5Stack CoreS3 Lite (ESP32S3)](https://docs.m5stack.com/) | 1 | システム制御用[span_5](start_span)[span_5](end_span)[span_6](start_span)[span_6](end_span) |
| リレーモジュール | M5Stack用 ミニリレーユニット | 1 | パルス制御用[span_7](start_span)[span_7](end_span) |
| USBサウンドカード | startech.com 96KHz/24-bit Hi-Fi | 1 | 信号のデジタル化・PC取り込み用[span_8](start_span)[span_8](end_span)[span_9](start_span)[span_9](end_span) |
| 変換アダプタ | BNCプラグ → 3.5mm モノラルプラグ | 1 | サウンドカードへの接続用[span_10](start_span)[span_10](end_span) |

### 2. アンプ・信号処理回路
| 部品名 | 型番・仕様 | 数量 | 備考 |
| :--- | :--- | :--- | :--- |
| 超低歪低雑音オペアンプ | Analog Devices AD797BRZ | 2 | 微小信号の増幅（表面実装部品）[span_11](start_span)[span_11](end_span)[span_12](start_span)[span_12](end_span) |
| SOP8-DIP8変換基板 | 一般的なSOP8ピッチ変換基板 | 2 | AD797BRZをブレッドボードで扱うため必須[span_13](start_span)[span_13](end_span)[span_14](start_span)[span_14](end_span) |
| NchパワーMOSFET | 東芝 2SK4017(Q) (60V/5A) | 2 | コイル電流のスイッチング用[span_15](start_span)[span_15](end_span) |
| ファストリカバリダイオード | 京セラ 20NFA40 (400V/2A) | 1 | フライホイールダイオードとして使用[span_16](start_span)[span_16](end_span) |
| フィルムコンデンサ | 0.047μF, 1μF, 2.2μF, 4.7μF | 各3 | ノイズ対策・フィルタリング用[span_17](start_span)[span_17](end_span)[span_18](start_span)[span_18](end_span) |
| コンデンサキット | SparkFun SFE-KIT-13698 | 1 | 容量調整用[span_19](start_span)[span_19](end_span) |
| 抵抗・LED類 | 各種抵抗器、砲弾型LED | 複数 | 動作確認および回路構成用[span_20](start_span)[span_20](end_span)[span_21](start_span)[span_21](end_span) |
| ブレッドボード | EIC-102BJ ＆ ジャンパーワイヤ | 1式 | プロトタイピング用[span_22](start_span)[span_22](end_span)[span_23](start_span)[span_23](end_span) |
| ユニバーサル基板 | 両面スルーホール Bタイプ (95×72mm) | 2 | 本組み実装用[span_24](start_span)[span_24](end_span)[span_25](start_span)[span_25](end_span) |

### 3. センサーコイル・サンプル
| 部品名 | 型番・仕様 | 数量 | 備考 |
| :--- | :--- | :--- | :--- |
| エナメル線 (2UEW) | 0.5mm 500g | 4 | センサーコイルの手巻き用[span_26](start_span)[span_26](end_span)[span_27](start_span)[span_27](end_span) |
| 透明塩ビパイプ | VP40 (内径41mm / 外径48mm) | 1 | コイルのボビンとして使用[span_28](start_span)[span_28](end_span)[span_29](start_span)[span_29](end_span) |
| 観測用サンプル | 高純度精製水 (脱イオン水) | 1 | プロトンの観測対象[span_30](start_span)[span_30](end_span) |

### 4. 電源系
| 部品名 | 型番・仕様 | 数量 | 備考 |
| :--- | :--- | :--- | :--- |
| 鉛蓄電池 | LONG WP12-12 (12V 12Ah) | 1 | 偏極コイルへの大電流供給用[span_31](start_span)[span_31](end_span)[span_32](start_span)[span_32](end_span) |
| アルカリ乾電池 | 9V角形 ＆ タカチ BH-9Vホルダー | 2 | アンプ回路用（ノイズ低減のため独立電源）[span_33](start_span)[span_33](end_span)[span_34](start_span)[span_34](end_span) |
| ヒューズ ＆ ホルダー | 平形ヒューズ 5A ＆ 15A対応ホルダー | 1式 | 短絡保護用[span_35](start_span)[span_35](end_span) |

### 5. 筐体・配線・その他
| 部品名 | 型番・仕様 | 数量 | 備考 |
| :--- | :--- | :--- | :--- |
| アルミダイキャストケース | RS Pro (222.1 x 145.9 x 55.9mm) | 1 | 電磁シールド筐体[span_36](start_span)[span_36](end_span)[span_37](start_span)[span_37](end_span) |
| BNC同軸関連 | 1.5D-2Vケーブル ＆ 基板取付用ジャック | 2 | 信号引き回し時のノイズ対策[span_38](start_span)[span_38](end_span)[span_39](start_span)[span_39](end_span) |
| 配線材 | AWG18 UL1007 耐熱ビニル絶縁電線 | 1式 | 電源や大電流ライン用[span_40](start_span)[span_40](end_span)[span_41](start_span)[span_41](end_span) |
| 接続端子 | ファストン端子 (#187) | 1式 | 鉛蓄電池との接続用[span_42](start_span)[span_42](end_span) |
| ワニ口クリップケーブル | 一般的なテスト用ケーブル | 1式 | 基板の仮組みやテスト接続に必須[span_43](start_span)[span_43](end_span) |
| 工具・消耗品 | パイプカッター、布テープ、結束バンド | 1式 | コイル製作・組み上げ用[span_44](start_span)[span_44](end_span) |
