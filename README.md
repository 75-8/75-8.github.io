# portal

GitHub Pages で公開する、GBP/JPY 中心の静的マーケットダッシュボードです。

## 概要

- OANDAで利用していた主要5機能（Order Book / Volatility / Value at Risk / Price Comparison / VaR on Chart）を、静的サイトで扱える形式に再構成
- TradingView ウィジェット（テクニカル分析 / 経済イベント）を併用
- サーバーサイドを使わず、GitHub Pages 上で完結して動作

## OANDA機能の代替実装

- Order Book → Market Pressure（上昇/下落日数比を BUY/SELL バー化）
- Volatility → 20日ヒストリカルボラティリティ（年率換算）
- Value at Risk → ヒストリカル法で 95% / 99% VaR 算出
- Price Comparison → GBP/JPY, USD/JPY, EUR/JPY のクロス比較
- VaR on Chart → GBP/JPY 終値ライン + 95%VaR 閾値ライン

## データソース

- Frankfurter API（為替時系列）
  - `https://api.frankfurter.app/`
- TradingView 埋め込みウィジェット
  - テクニカル分析 / 経済イベント

## ハーネス設計

金融投資アイデアの検証フローを分離したハーネスを `harness/` 配下に作成しています。

- `harness/README.md`: 運用ルールと全体構造
- `harness/01_idea_backlog`〜`09_review`: ライフサイクル別の保管場所
- `harness/templates`: 仮説 / バックテスト / レビュー テンプレート

## ファイル構成

```text
.
├── harness/
├── index.html
├── styles.css
├── plan.md
├── README.md
└── LICENSE
```

## 注意

- 本リポジトリは静的配信前提です（サーバーサイド処理なし）。
- 外部API障害時は一部カードが「取得失敗」表示になります。

## ライセンス

`LICENSE` を参照してください。
