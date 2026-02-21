# portal

GitHub Pages で公開できる、GBP/JPY 中心の静的マーケットダッシュボードです。

## 目的

以前の OANDA 埋め込み（`widget.oanda.jp`）は GitHub Pages 上で接続拒否となるため、
**同等機能を静的実装 + TradingView 補助で代替**しています。

## OANDA機能と代替実装（Plan）

- Order Book → 「Market Pressure」
  - 直近リターンの上昇/下落日数比を BUY/SELL バーで可視化
- Volatility → ヒストリカルボラティリティ
  - 20日リターンの標準偏差を年率換算
- Value at Risk → ヒストリカル VaR
  - リターン分布から 95% / 99% VaR を算出
- Price Comparison → クロスレート比較
  - GBP/JPY, USD/JPY, EUR/JPY を同一データから表示
- VaR on Chart → ラインチャート + VaR 閾値ライン
  - GBP/JPY 終値系列に 95%VaR 水準を重ねて表示

## データソース

- Frankfurter API（為替時系列）
  - `https://api.frankfurter.app/`
- TradingView 埋め込みウィジェット
  - テクニカル分析 / 経済イベント

## ファイル構成

```text
.
├── index.html
├── styles.css
├── README.md
└── LICENSE
```

## ローカル確認

```bash
python3 -m http.server 8000
```

ブラウザで <http://localhost:8000> を開きます。

## 注意

- 本リポジトリは静的配信前提です（サーバーサイド処理なし）。
- 外部API障害時は一部カードが「取得失敗」表示になります。

## ライセンス

`LICENSE` を参照してください。
