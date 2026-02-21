# portal

`portal` は、**GBP/JPY（ポンド円）を中心とした相場情報を 1 ページに集約表示するシンプルな静的ページ**です。

`index.html` では、OANDA と TradingView の埋め込みウィジェットを読み込み、注文状況・ボラティリティ・VaR・価格比較・テクニカル分析・経済イベントをまとめて確認できる構成になっています。

## 主な機能

- OANDA Order Book（注文情報）
- OANDA Volatility（ボラティリティ）
- OANDA Value at Risk（VaR）
- OANDA Price Comparison（価格比較）
- OANDA VaR on Chart（チャート上の VaR）
- TradingView Technical Analysis（テクニカル分析）
- TradingView Events（経済イベント）

## 技術構成

- HTML（`index.html`）
- 外部埋め込みスクリプト
  - `widget.oanda.jp`
  - `s3.tradingview.com`

## ファイル構成

```text
.
├── index.html
├── LICENSE
└── README.md
```

## 使い方

### 1. ローカルで開く

最小構成の静的ページなので、`index.html` をブラウザで直接開くだけでも表示できます。

### 2. ローカルサーバーで確認する（推奨）

埋め込みウィジェットの読み込みや検証のため、簡易サーバーでの確認を推奨します。

```bash
python3 -m http.server 8000
```

その後、ブラウザで以下へアクセスします。

- <http://localhost:8000>

## カスタマイズ

`index.html` 内の各ウィジェット設定 JSON を変更することで、以下を調整できます。

- 通貨ペア（例: `GBP_JPY` / `OANDA:GBPJPY`）
- 表示サイズ（`width`, `height`）
- ロケール（`locale`）
- カラーテーマ（`colorTheme`）
- テクニカル分析の時間足（`interval`）

## 注意事項

- 本ページは外部サービスのウィジェットに依存するため、インターネット接続が必要です。
- ウィジェット仕様の変更や配信元の障害により、表示内容が変わる可能性があります。
- 投資判断は自己責任で行ってください。

## ライセンス

ライセンス情報は `LICENSE` を参照してください。
